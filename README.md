# C

# lessons 2
# Ветвление if-else
Встречаются ситуации, когда программе нужно выбрать, какую операцию ей выполнить, в зависимости от определенного условия.

К примеру, мы вводим с клавиатуры целое число. Если это число больше десяти, то программа должна выполнить одно действие, иначе — другое. Реализуем этот алгоритм на C++ с помощью конструкции ветвления. 

Оператор **if** служит для того, чтобы выполнить какую-либо операцию в том случае, когда условие является верным. Условная конструкция в С++ всегда записывается в круглых скобках после оператора **if**.

Внутри фигурных скобок указывается тело условия. Если условие выполнится, то начнется выполнение всех команд, которые находятся между фигурными скобками. Else - инача происходит другое.
Пример:
```C++
if ( условие ) {
  // тело условия
} 
else {
  // тело иначе
}
```

При необходимости если нужно проверить несколько условий, то используем оператор else if ( .. ) - "иначе если".

```C++
if (num < 10) {  // Если введенное число меньше 10.
    cout << "Это число меньше 10." << endl;
} 
else if (num == 10) {
    cout << "Это число равно 10." << endl;
} 
else {  // иначе
    cout << "Это число больше 10." << endl;
}
```
# Switch-case
Другую форму организации ветвления программ представляет конструкция switch...case. Она имеет следующую форму:
```C++
switch(выражение) {
    case константа_1: инструкции_1;
    case константа_2: инструкции_2;
     
    default: инструкции;
}
```
После ключевого слова switch в скобках идет сравниваемое выражение. Значение этого выражения последовательно сравнивается со значениями после оператора сase. И если совпадение будет найдено, то будет выполняться определенный блок сase.

В конце конструкции switch может стоять блок default. Он необязателен и выполняется в том случае, если значение после switch не соответствует ни одному из операторов case. Например:
```C++
#include <iostream>
 
int main() {
    int x = 2; 
    switch(x) {
        case 1: 
            std::cout << "x = 1" << "\n";
            break;
        case 2: 
            std::cout << "x = 2" << "\n";
            break;
        case 3: 
            std::cout << "x = 3" << "\n";
            break;
        default: 
            std::cout << "x is undefined" << "\n";
            break;
    }
    return 0;
}
```
# Циклы
Иногда необходимо повторять одно и то же действие несколько раз подряд. Для этого используют циклы. Циклы в С++: 
  1. for
  2. while
  3. do while

Если мы знаем точное количество действий (итераций) цикла, то можем использовать цикл for. Синтаксис его выглядит примерно так:
```C++
for (действие до начала цикла; условие продолжения цикла; действия в конце каждой итерации цикла) {
         инструкция цикла;
         инструкция цикла 2;
         ...
         инструкция цикла N;
}
```
проще говоря так:
```C++
for (счетчик = значение; счетчик < значение; шаг цикла) {
    тело цикла;
}
```

Счетчик цикла — это переменная, в которой хранится количество проходов данного цикла. 
Пример с for:
```C++
#include <iostream>
using namespace std;

int main() {
    int sum = 0; // сумма чисел от 1 до 1000.
    for (int i = 1; i <= 1000; i++) // задаем начальное значение 1, конечное 1000 и задаем шаг цикла - 1.
    {
        sum = sum + i;
    }
    cout << "Сумма чисел от 1 до 1000 = " << sum << endl;         
    return 0;
}
```
Когда мы не знаем, сколько итераций должен произвести цикл, нам понадобится цикл while или do...while. Синтаксис цикла while в C++ выглядит следующим образом.
```C++
while (Условие) {
    Тело цикла;
}
```

Пример с while:
```C++
#include <iostream>
using namespace std;

int main()
{
    int i = 0; // инициализируем счетчик цикла.
    int sum = 0; // инициализируем счетчик суммы.
    while (i < 1000)
    {
        i++;
        sum += i;
    }
    cout << "Сумма чисел от 1 до 1000 = " << sum << endl; 
    return 0;
}
```
После компиляции программа выдаст результат, аналогичный результату работы c for.

Цикл do while очень похож на цикл while. Единственное их различие в том, что при выполнении цикла do while один проход цикла будет выполнен независимо от условия. Решение задачи на поиск суммы чисел от 1 до 1000, с применением цикла do while.

```C++
#include <iostream>
using namespace std;

int main ()
{
    int i = 0; // инициализируем счетчик цикла.
    int sum = 0; // инициализируем счетчик суммы.
    do {// выполняем цикл.
        i++;
        sum += i;
    } while (i < 1000); // пока выполняется условие.
    cout << "Сумма чисел от 1 до 1000 = " << sum << endl;
    return 0;
}
```
Принципиального отличия нет, но если присвоить переменной i значение, большее, чем 1000, то цикл все равно выполнит хотя бы один проход.

# Массивы
Массив — это область памяти, где могут последовательно храниться несколько значений.

Возьмем группу студентов из десяти человек. У каждого из них есть фамилия. Создавать отдельную переменную для каждого студента — не рационально. Создадим массив, в котором будут храниться фамилии всех студентов. 

В std есть специальный тип std::string ( если усложненым языком - Строки — это объекты, представляющие последовательности символов.
Стандартный строковый класс обеспечивает поддержку таких объектов с интерфейсом, аналогичным интерфейсу стандартного контейнера байтов, но с добавлением функций, специально предназначенных для работы со строками однобайтовых символов. ) простыми словами тип данных для строк.

При создании статического массива, для указания его размера может использоваться только константа. Размер выделяемой памяти определяется на этапе компиляции и не может изменяться в процессе выполнения.

Выделение памяти в процессе выполнения возможно при работе с динамическими массивами. Но о них немного позже.

Синтаксис создания статического массива:
```C++
тип_данных название_массива[размер];
```

Пример ( строки ):
```C++
#include <iostream>
#include <string>

int main() {
    std::string students[10] = {
        "Иванов", "Петров", "Сидоров",
        "Ахмедов", "Ерошкин", "Выхин",
        "Андеев", "Вин Дизель", "Картошкин", "Чубайс"
    };
    std::cout << students << std::endl; // Пытаемся вывести весь массив непосредственно
    return 0;
}
```
Скомпилируйте этот код и посмотрите, на результат работы программы. Готово? А теперь запустите программу еще раз и сравните с предыдущим результатом. В моей операционной системе вывод был следующим:

    1. Первый вывод: 0x7ffff8b85820
    2. Второй вывод: 0x7fff7a335f90
    3. Третий вывод: 0x7ffff847eb40

Мы видим, что выводится адрес этого массива в оперативной памяти, а никакие не «Иванов» и «Петров».

Дело в том, что при создании переменной, ей выделяется определенное место в памяти. Если мы объявляем переменную типа int, то на машинном уровне она описывается двумя параметрами — ее адресом и размером хранимых данных.

Массивы в памяти хранятся таким же образом. Массив типа int из 10 элементов описывается с помощью адреса его первого элемента и количества байт, которое может вместить этот массив. Если для хранения одного целого числа выделяется 4 байта, то для массива из десяти целых чисел будет выделено 40 байт.
```C++
#include <iostream>
#include <string>

int main() {    
    std::string students[10] = {
        "Иванов", "Петров", "Сидоров",
        "Ахмедов", "Ерошкин", "Выхин",
        "Андеев", "Вин Дизель", "Картошкин", "Чубайс"
    };
    std::cout << students[0] <<  std::endl;
    return 0;
}
```
вывод всех элементов массива через цикл:
```C++
#include <iostream>
#include <string>

int main() {
    std::string students[10] = {
        "Иванов", "Петров", "Сидоров",
        "Ахмедов", "Ерошкин", "Выхин",
        "Андеев", "Вин Дизель", "Картошкин", "Чубайс"
    };  
    for (int i = 0; i < 10; i++) {
        std::cout << students[i] << std::endl;
    }

    return 0;
}
```

Заполнение массива с клавиатуры:
```C++
#include <iostream>
#include <string>
using namespace std;

int main() {    
        int arr[10];
        
        // Заполняем массив с клавиатуры
        for (int i = 0; i < 10; i++) {
            cout << "[" << i + 1 << "]" << ": ";
            cin >> arr[i];
        }

        // И выводим заполненный массив.
        cout << "\nВаш массив: ";

        for (int i = 0; i < 10; ++i) {
            cout << arr[i] << " ";
        }
        cout << endl;
        return 0;
}
```
