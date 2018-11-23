## lessone 1

var -> function
let -> block
const -> block

## lessone 2

var -> function
let -> block
const -> block

## lessone 3

```
const person = {
name: "Mosh",
walk: function() {},
talk() {}
};

console.log(person);
person.talk();
const propertyMember = "name";
person[propertyMember] = "John";
console.log(person);
```

## lessone 4 'this'

```
const person = {
name: "Mosh",
walk() {
console.log(this);
}
};

person.walk();

const walk = person.walk;
walk();//For strict mode here this is undified, for not strict mode, this is window object. Because here walk is a stand along method.
```

## lessone 5 Binding this

```
const person = {
name: "Mosh",
walk() {
console.log(this);
}
};

person.walk();

const walk = person.walk.bind(person); //bind(object) will return a new object, and set this in walk() to be the new created object.
walk();
```

## lessone 6 Arrow Functions

```
const square = name => console.log(name + name);

square("Babel");

const jobs = [
{ id: 1, isActive: true },
{ id: 1, isActive: true },
{ id: 1, isActive: false }
];

const activeJobs = jobs.filter(job => job.isActive === true);

console.log(activeJobs.length);
for (let i = 0; i < activeJobs.length; i++) {
console.log(activeJobs[i]);
}
```

## lessone 7 Arrow Functions

In lambda, don't rebind 'this' keyword.

```
const person = {
talk() {
setTimeout(() => console.log("This", this), 5000); //Here, this will not rebind to stand alone function.
}
};

person.talk();
```

## lessone 8 Array.map method

```
const colors = ["red", "green", "blue"];
const items = colors.map(color => "<li>" + color + "<li>"); //concatenate
const items1 = colors.map(color => `<li>${color}<li>`); // \${} argument place holder, this is a template literal, will be dynamically rendered
console.log(items);
console.log(items1);
```

## lessone 9 Object Destructuring

```
const address = {
street: "",
city: "",
country: ""
};

address.street = "753 S";
address.city = "chicago";
address.country = "US";

// const street = address.street;
// const city = address.city;
// const country = address.country;

// const { street, city, country } = address;
// console.log(street);
// console.log(city);
// console.log(country);

// const { street: st } = address; //alias
// console.log(st);

const { street } = address;
console.log(street);
```

## lessone 10 Spread Operator

```
const first = [1, 2, 3];
const second = [1, 2, 3];
// const combined = first.concat(second);

// const combined = [...first, ...second];
const combined = [...first, "a", 10, ...second, "12"];
console.log(combined);

const myName = {
name: "Mosh"
};

const myAge = {
age: 9
};

const person = { ...myName, ...myAge, gender: "male" };
console.log(person);
```

## lessone 11 Classes

```
class Person {
walk() {
console.log("walk!");
}

constructor(name) {
this.name = name;
}
}

const mosh = new Person("Mosh");
console.log(mosh);
```

## lessone 12 Inheritance

```
class Teacher extends Person {
teach() {
console.log("Teach");
}

constructor(name, degree) {
super(name);
this.degree = degree;
}
}

const teacher = new Teacher("Mosh", "Class 1");
teacher.walk();
teacher.teach();
```

## lessone 13 Modules

//Put class into different js files:
// teacher.js, person.js

```
export class Person {
walk() {
console.log("walk!");
}

constructor(name) {
this.name = name;
}
}

import {Person} from './person' //just file name without extension

export class Teacher extends Person {
teach() {
console.log("Teach");
}

constructor(name, degree) {
super(name);
this.degree = degree;
}
}
```

## lessone 14 Named and Default Exports

// named exports could be a class, or a function.
//default export -> import Teacher from "./teacher";
//named export -> import {Teacher} from "./teacher";
//combined -> import Teacher {promote} from "./teacher";

```
export promote = function(){};
export default class Teacher extends Person {
teach() {
console.log("Teach");
}

constructor(name, degree) {
super(name);
this.degree = degree;
}
}
```
