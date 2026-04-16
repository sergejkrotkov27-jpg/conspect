# Полный конспект: Указатели, массивы, ООП (C++)

## 1. Указатели (Pointers)

Указатель — переменная, хранящая адрес памяти другой переменной.

```cpp
int a = 42;
int *p = &a;   // p = адрес a
cout << *p;    // разыменование -> 42
*p = 100;      // a теперь 100
cpp
int *ptr = nullptr;  // безопасный нулевой указатель
if (ptr == nullptr) {
    cout << "Указатель пуст";
}
cpp
int arr[3] = {10, 20, 30};
int *p = arr;        // указывает на arr[0]
cout << *(p + 1);    // 20
2. Передача массива в функцию
Массив не копируется — передаётся указатель на первый элемент.

cpp
void multiply(int *arr, int size, int factor) {
    for (int i = 0; i < size; i++) {
        arr[i] *= factor;
    }
}

int main() {
    int data[] = {1, 2, 3, 4};
    multiply(data, 4, 10);
    // data стал {10, 20, 30, 40}
}
3. Основы ООП
Принцип	Что означает
Инкапсуляция	Скрытие внутренних деталей
Наследование	Создание нового класса на основе существующего
Полиморфизм	Один интерфейс — разная реализация
4. Понятие класса
cpp
class BankAccount {
private:
    double balance;
    string owner;

public:
    BankAccount(string name, double startBalance) {
        owner = name;
        balance = startBalance;
    }

    void deposit(double amount) {
        if (amount > 0) balance += amount;
    }

    double getBalance() const {
        return balance;
    }
};

int main() {
    BankAccount acc("Alice", 1000);
    acc.deposit(500);
    cout << acc.getBalance();  // 1500
}
5. Наследование в ООП
cpp
class Animal {
protected:
    string name;
public:
    Animal(string n) : name(n) {}
    void eat() { cout << name << " eats\n"; }
};

class Dog : public Animal {
public:
    Dog(string n) : Animal(n) {}
    void bark() { cout << name << " barks: Woof!\n"; }
};

int main() {
    Dog d("Rex");
    d.eat();   // от Animal
    d.bark();  // своё
}
6. Полиморфизм (переопределение методов)
cpp
class Animal {
public:
    virtual void sound() { cout << "...\n"; }
    virtual ~Animal() {}
};

class Cat : public Animal {
public:
    void sound() override { cout << "Meow!\n"; }
};

void makeSound(Animal *a) {
    a->sound();
}

int main() {
    Cat c;
    makeSound(&c);  // "Meow!"
}
7. Быстрая шпаргалка
cpp
// Указатель
int *p = &x;   *p = 5;

// Массив в функцию
void f(int arr[], int n);

// Класс
class A {
private: int x;
public: void set(int v) { x = v; }
};

// Наследование
class B : public A {};

// Полиморфизм
virtual void foo() override;
