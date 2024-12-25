### JAVASCRIPT:

**ES7:** exponential 2**3, array.incluses, Object.entries, Object.values,

**Closures:**
A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives a function access to its outer scope.
Ex:
function init() {
  var name = "Mozilla";
  function displayName() {
    console.log(name); 
  }
  return displayName;
}
let getName = init();
getName();


**Polyfill:** In JavaScript, a polyfill is a piece of code that provides modern functionality to older browsers that don't natively support it. It essentially "fills in" the gap, allowing you to use newer features without worrying about browser compatibility.

**Recursion:**
A recursive function is a function that calls itself somewhere within the body of the function.
We need a condition to break the recursion.
Ex:
```
const factorial = num => { 
  if(num==1){
    return 1;
  } else {
    return num * factorial(num-1-1)
  }
}
factorial(5);
```

**Bind:**
The Bind creates a new function and when that new function is called it set this keyword to the first argument which is passed to the bind method, and if any other sequences of arguments preceding the first argument are passed to the bind method then they are passed as an argument to the new function when the new function is called.
Ex:let nameObj = { name: 'sri' };
const printName = { name: 'ramana', print: function(){ console.log(this.name); } }
bindEx = printName.print.bind(nameObj);
bindEx(); // sriprintName.print() // ramana
Ex2:
let nameObj = { name: 'sri' };
printName2 =  function(){ console.log(this.name); }
bindEx2 = printName.bind(nameObj);
bindEx2()
// VM577:3 Uncaught TypeError: printName.bind is not a function
//    at <anonymous>:3:21

Ex3: (Polyfill)let nameObj = {
    name: "Tony"
}

let PrintName = {
    name: "steve",
    sayHi: function () {
        console.log(this.name);
    }
}

Object.prototype.MyBind = function (bindObj) {
    console.log(bindObj); // {name: 'Tony'}
    console.log(this); // ƒ () {   console.log(this.name); }
    // Here "this" will be sayHi function
    bindObj.myMethod = this;
    return function () {
        bindObj.myMethod();
    }
}
let HiFun = PrintName.sayHi.MyBind(nameObj);
HiFun();
￼
Ex4: (Polyfill with args)
let nameObj = {
    name: "Tony"
}

let PrintName = {
    name: "steve",
    sayHi: function (age) {
        console.log(this.name + " age is " + age);
    }
}

Object.prototype.MyBind = function (bindObj, ...args) {
    bindObj.myMethod = this;
    return function () {
        bindObj.myMethod(...args);
    }
}
let HiFun = PrintName.sayHi.MyBind(nameObj, 42);
HiFun();

**Debouncing:**
Debouncing is a strategy used to improve the performance of a feature by controlling the time at which a function should be executed.URL : https://www.freecodecamp.org/news/deboucing-in-react-autocomplete-example/
Ex:function debounce(dfunc,delay){
let timeout = null;
return (...args) => {
    if(timeout)
        clearTimeout(timeout);
    timeout = setTimeout(()=>{ dfunc(...args) },delay);
}
}
print=(message)=>{console.log('message',message)};
dPrint = debounce(print,2000);// Execution below at 1sec interval
setTimeout(()=>{ console.log('at 1 sec'); dPrint('hello1')},1000);
setTimeout(()=>{ console.log('at 2 sec'); dPrint('hello2')},2000);
setTimeout(()=>{ console.log('at 3 sec'); dPrint('hello3')},3000);

￼



**Throttle:**
Throttling is a technique used to limit the rate at which a function is called. Throttling transforms a function such that it can only be called once in a specific interval of time.https://www.freecodecamp.org/news/throttling-in-javascript/
Ex:
function throttle(dFunc,delay){
    let timeout = null;

    return (...args) => {
        if(!timeout){
            dFunc(...args);
            timeout = setTimeout(()=> {timeout=null},delay)
        }
    }
}
print = message => { console.log('message',message) }
tPrint = throttle(print,1000);
tPrint('hello1')
tPrint('hello2')
setTimeout(()=>{tPrint('hello3')},500);
setTimeout(()=>{tPrint('hello4')},1200);
￼


**Object.groupBy:**
const inventory = [
  { name: "asparagus", type: "vegetables", quantity: 5 },
  { name: "bananas", type: "fruit", quantity: 0 },
  { name: "goat", type: "meat", quantity: 23 },
  { name: "cherries", type: "fruit", quantity: 5 },
  { name: "fish", type: "meat", quantity: 22 },
];
const result = Object.groupBy(inventory, ({ type }) => type);

/* Result is:
{
  vegetables: [
    { name: 'asparagus', type: 'vegetables', quantity: 5 },
  ],
  fruit: [
    { name: "bananas", type: "fruit", quantity: 0 },
    { name: "cherries", type: "fruit", quantity: 5 }
  ],
  meat: [
    { name: "goat", type: "meat", quantity: 23 },
    { name: "fish", type: "meat", quantity: 22 }
  ]
}
*/



**OOPS:**
OBJECT:An Object is a unique entity that contains properties and methods. It is close to represent real life objects like to define a person height, age, name etc we can use properties where as to perform an action we can use methods.

**CLASS:**
Classes are blueprints of an Object. A class can have many Objects because the class is a template while Objects are instances of the class or the concrete implementation. 

JavaScript classes, introduced in ECMAScript 2015, are primarily syntactical sugar over JavaScript’s existing prototype-based inheritance. The class syntax is not introducing a new object-oriented inheritance model to JavaScript. JavaScript classes provide a much simpler and clearer syntax to create objects and deal with inheritance. 



