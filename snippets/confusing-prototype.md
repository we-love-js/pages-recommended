Taken from [webreflection.blogspot.com](http://webreflection.blogspot.com/2009/06/wait-moment-javascript-does-support.html)
---------------------------------------
```javascript
// generic constructor
function B(){};

// remember the prototype
var B1proto = B.prototype;

// B instance
var b1 = new B;

// prototype reassignment
B.prototype = {
    constructor:B
};

// remember new prototype
var B2proto = B.prototype;

// B instance
var b2 = new B;

alert(b2 instanceof B); // true
alert(b1 instanceof B); // false
```

Above snippet demonstrates how inheritance and instanceof are related to the current prototype, rather than the function/constructor itself.
In few words, the function is the implicit init method for the current prototype object. The relation, as we could spot with FireFox, is with the prototype and not the used constructor.

```javascript
// FireFox exposes __proto__
// will be Object.getPrototypeOf
// in ECMAScript 3.1
b1.__proto__ == B1proto; // true
b2.__proto__ == B2proto; // true
```
