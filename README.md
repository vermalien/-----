#include <iostream>
#include <limits>
#include <string>
#include <vector>
enum Moves { KAMEN = 0, NOJNICI, BUMAGA };

int main() {

std::vector<Moves> computerMoves {
Moves::KAMEN, Moves::KAMEN, Moves::BUMAGA, Moves::KAMEN, Moves::NOJNICI, Moves::KAMEN,
Moves::BUMAGA, Moves::NOJNICI, Moves::KAMEN, Moves::KAMEN, Moves::KAMEN, Moves::NOJNICI,
Moves::KAMEN, Moves::KAMEN, Moves::NOJNICI
};

std::vector<std::string> nameMoves {
"камень", "ножницы", "Бумага"
};

std::string answer { "да" };

size_t countDraw { 0 };
size_t countComputerWins { 0 };
size_t countPlayerWins { 0 };

short personMove { 0 };
short computerMove { 0 };

for (size_t i { 0 }; i < computerMoves.size(); ++i) {

system("clear");

std::cout<< "цу-е-фа:\n" << "1-Камень\n" << "2-Ножницы\n" << "3-Бумага\n";
do {

std::cin
>>personMove;

if (personMove < 1 || personMove > 3) {

std::cout
<< "Введи цифру от 1 до 3 ";

std::cin.clear();
std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
}

} while (personMove < 1 || personMove > 3);

computerMove = computerMoves.at(i);
--personMove;


short result = (computerMove - personMove) % 3;

switch (result < 0 ? result + 3 : result) {

case 0:
std::cout<< "НИЧЬЯ"<< std::endl;

++countDraw;
break;

case 1:
std::cout << "ПОБЕДА" << std::endl;
++countPlayerWins;
break;

case 2:
std::cout << "ПОРАЖЕНИЕ" << std::endl;
++countComputerWins;
break;
}
   std::cout
            << "Чтобы продолжить введите да:\n" << "чтобы завершить игру введите нет:\n ";
            std::cin
            >> answer;
 
        if (answer == "нет") {
 
            system("clear");

    // std::cout
                // << "ПОРАЖЕНИЕ "  << i << "\n" << "ПОБЕДА " << i  << "\n" << "НИЧЬЯ " << i << "\n";
break;
}
}
return 0;
} 
