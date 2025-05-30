# Завдання 1
Клас Student, який містить три властивості: name, age та grade. Замість того, щоб оголошувати ці властивості в тілі класу, потім у конструкторі, і нарешті надавати їм значення, напишіть скорочену ініціалізацію.
```ts
class Student {
  public name: string;
  public age: number;
  public grade: string;

  constructor(name: string, age: number, grade: string) {
    this.name = name;
    this.age = age;
    this.grade = grade;
  }
}
```
# Завдання 2
Ваше завдання полягатиме у створенні двох класів – Employee та Manager.

Клас Employee повинен включати:

властивість name, яка буде доступна всім.
властивість department, яка буде доступна лише всередині класу Employee.
salary, яке буде доступне лише всередині класу Employee та його підкласів.


Клас Manager повинен бути підклас класу Employee

Необхідно реалізувати в класі Manager конструктор, який викликатиме конструктор суперкласу та збільшуватиме salary на 10000.
```ts
class Employee {
  // Заповніть модифікатори доступу
  name: string;
  department: string;
  salary: number;

  constructor(name: string, department: string, salary: number) {
    this.name = name;
    this.department = department;
    this.salary = salary;
  }

  getEmployeeDetails() {
    return `Name: ${this.name}, Department: ${this.department}, Salary: ${this.salary}`;
  }
}

class Manager extends Employee {
  // Реалізуйте конструктор та збільшіть salary на 10000
}
```
# Завдання 3
Ви створюєте гру, де є персонажі з різними ролями. Зараз ви працюєте над класом Wizard, який має реалізовувати два інтерфейси - ICharacter та ISpellCaster.

Визначте інтерфейси ICharacter та ISpellCaster так, щоб вони відповідали вимогам класу Wizard. Інтерфейс ICharacter повинен включати властивості name і level, і навіть метод introduce і levelUp. Інтерфейс ISpellCaster повинен включати метод castSpell.
```ts
// реалізація класу Wizard
class Wizard implements ICharacter, ISpellCaster {
  constructor(public name: string, public level: number) {
    if (this.level < 1) {
      throw new Error('Level too low');
    }
  }

  introduce(phrase: string): void {
    console.log(phrase + ', ' + this.name);
  }

  castSpell(): void {
    console.log('Casting a spell, behold my power!');
  }

  levelUp(): void {
    this.level++;
    console.log(`Level up! New level is ${this.level}`);
  }
}

// тестування класу
const wizard = new Wizard('Merlin', 15);

wizard.introduce('I am the mighty wizard');
wizard.castSpell();
wizard.levelUp();  // Level up! New level is 16
```
# Завдання 4 *
У цьому завдання вам належить реалізувати сценарій життя, де людина, ключ і будинок взаємодіють один з одним.

Ключ (Key): Створіть клас Key. У нього має бути одна приватна властивість signature, яка генерується випадково при створенні об'єкта цього класу (наприклад Math.random()). Також цей клас повинен мати метод getSignature, який повертає значення властивості signature.

Людина (Person): Створіть клас Person. Конструктор цього класу приймає об'єкт класу Key і зберігає їх у приватному властивості key. Клас Person повинен мати метод getKey, який повертає збережений ключ.

Дім (House): Створіть абстрактний клас House. Цей клас має дві властивості: door, яка може бути відкрита (true), або закрита (false), і key, яка зберігає об'єкт класу Key. У цьому класі також повинен бути метод comeIn, який додає об'єкт класу Person у масив tenants, якщо door відкрита. Ваш абстрактний клас House також повинен мати абстрактний метод OpenDoor, який приймає об'єкт класу Key.

Мій будинок (MyHouse): Створіть клас MyHouse, який успадковується від абстрактного класу House. Реалізуйте метод openDoor у цьому класі. Якщо ключ, переданий цьому методу, збігається з ключем, збереженим як key, то двері відчиняються.

Після реалізації всіх класів створіть об'єкти для кожного класу та спробуйте відтворити сценарій, в якому людина приходить додому.

Наприклад, ось так:

```ts
const key = new Key();

const house = new MyHouse(key);
const person = new Person(key);

house.openDoor(person.getKey());

house.comeIn(person);
```