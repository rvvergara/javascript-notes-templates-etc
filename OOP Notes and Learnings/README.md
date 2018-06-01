<h1>Definitive Guide to Object-Oriented Javascript Notes</h1>
<p>Notes I compiled from the awesome almost 30-minute tutorial by <a href="http://www.letscodejavascript.com/">Let's Code Javascript by James Shore</a></p>
<p>All images are screen shots of the video tutorial</p>
<p>
    <a href="https://youtu.be/PMfcsYzj-9M">Video link to the tutorial</a>
</p>

<h2>1. Object Basics</h2>
<p>
    <img src="./images/common-javascript-types.jpg" width="300">
</p>
<p>
    <img src="./images/javascript-primitive-types.jpg" width="300">
</p>
<p>
    <img src="./images/javascript-special-objects.jpg" width="300">
</p>
<p>
    <img src="./images/sample-object.JPG" width="600">
</p>
<p>
    <blockquote>
        Primitives are passed by value:
    </blockquote>
    <img src="./images/primitives-passed-by-value.JPG" width="600">
</p>
<p>
    <blockquote>
        Objects are passed by reference:
    </blockquote>
    <img src="./images/objects-passed-by-reference.JPG" width="600">
</p>
<p>
    <blockquote>
        Difference between an undefined property (explicitly set in the object) vs property is undefined
    </blockquote>
    <img src="./images/undefined-property-vs-property-is-undefined.JPG" width="600">
</p>
<h2>2. Functions and Methods</h2>
<p>
    <blockquote>When a function is defined, Javascript creates an object w/ 3 predetermined properies: name, length and prototype</blockquote>
    <img src="./images/function-object1.JPG" width="700">
</p>
<p>
    <blockquote>Functions are just like regular objects. They are passed by reference</blockquote>
</p>
<p>
    <blockquote>When a function is inside an object, it's called a method. When a method is run, 'this' refers to the object that called it</blockquote>
    <img src="./images/function-as-method.JPG" width="700">
</p>
<p>
    <img src="./images/this-object-that-called.JPG" width="700">
</p>
<p>
    <strong>Explicit binding: is when the context of 'this' is chosen using:</strong>
    <ol>
        <li>call: immediately invoked -> fn.call(thisArg,a,b,c...)->e.g myMethod.call(objec1); //42</li>
        <li>apply: immediately invoked -> fn.apply(thisArg,[a,b,c...])</li>
        <li>bind: returns a function def -> fn.bind(thisArg,a,b,c,d...)-> 
        useful when using asynchronous functions (or functions called later) and when we do not know the exact arguments</li>
    </ol>
</p>
<h2>3. Prototypal Inheritance</h2>
<p>
    <blockquote>It's rare that all objects will be declared from scratch because there will be some repeated patterns</blockquote>
    <img src="./images/all-objects-declared-from-scratch.JPG" width="700">
    <blockquote>What is done then is use a <em>prototype</em>. This works by defining a single object and have other objects inherit from it or <em>extend</em> it.</blockquote>
    <img src="./images/prototype-inheritance1.JPG" width="700">
</p>
<h3>Every single object has a prototype except for the base <code>Object</code> or any object created that explicitly set not to have a prototype</h3>
<p>Note: [[Prototype]] in the figure is the same as __proto__</p>
<p>
        <img src="./images/prototype-inheritance2.JPG" width="700">
</p>
<h2>4. Polymorphism and Method Overriding</h2>
<img src="./images/polymorphism1.JPG" width="700">
<p><img src="./images/polymorphism2.JPG" width="700"></p>
<h2>5. Classes and Instantiation</h2>
<p>The common way to organize Javascript objects is separating data from methods</p>
<p><img src="./images/instantiation1.JPG" width="800"></p>
<blockquote><strong>Creating an instance is called <em>instantiation:</em></strong>
    <ul>
            <li>Classes/prototypes are about the method</li>
            <li>Instances are about the data</li>
        </ul>
</blockquote>
<p><img src="./images/instantiation2.JPG" width="800" style="border:1px solid black"></p>
<blockquote><strong>Instantiation is a 2-step process:</strong>
    <ol>
        <li>Creating the object/instance by extending the prototype through Object.create()</li>
        <li>Initialize its data</li>
    </ol>
</blockquote>
<p><img src="./images/instantiation3.JPG" width="800" style="border:1px solid black"></p>
<p><blockquote>But:</blockquote>
    <img src="./images/instantiation4.JPG" width="800" style="border:1px solid black">
</p>
<h4><p>One of the nice things about OOP is that it allows you to decide how your data is going to be stored in a way that nobody else has to worry about it.</p>
<p>
    You just provide access to that data through your methods and then, if you want to change the way data is stored, then you just update your object's methods - but you don't have to update all the rest of the program.
</p></h4>
<h4>
    <p>What's really common is to use some sort of initialization function. We call this <em>a Constructor</em>.</p>
    <p>This is a common method used to initialize objects</p>
</h4>
<img src="./images/instantiation5.JPG" width="800" style="border:1px solid black">
<h2>6. The Classical Model</h2>
<h4>When a function is defined, Javascript creates an object w/ name, length and prototype properties.</h4>
<p>Such prototype property points to an object w/ a constructor property that points back to the function</p>
<img src="./images/classical1.JPG" width="800" style="border:1px solid black">
<p>So whenever a function is defined, two objects are actually created: the function object and the function's prototype object</p>
<p><strong>So whenever a function is defined, a constructor is actually being defined that's associated with a do-nothing class:</strong></p>
<img src="./images/classical2.JPG" width="800" style="border:1px solid black">
<p>If a function is meant to be a constructor its name should start with a capital letter (convention)</p>
<p>To create an instance of an object in the classical model, the <code>new</code> keyword is used</p>
<p>If <code>new</code> is used in a constructor function this will:</p>
<ul>
    <li>Create an empty object</li>
    <li>Sets <code>this</code> to be that empty object</li>
    <li>Implicitly returns <code>this</code> object</li>
    <li>Adds a <code>__proto__</code> property to that returned object which links the prototype property of the constructor function to the new object</li>
</ul>
<p>Compared to each other, Prototypal (top) and Classical (bottom):</p>
<img src="./images/classical3.JPG" width="800" style="border:1px solid black">
<p>Classical model with subclasses:</p>
<img src="./images/classical4.JPG" width="800" style="border:1px solid black">
<p>Prototypal inheritance and Classical model side-by-side:</p>
<img src="./images/classical5.JPG" width="800" style="border:1px solid black">
<h2>7. instanceof</h2>
<p>It's often convenient to know which class was used to instantiate an object - <code>instanceof</code> keyword is used</p>
<p>The way <code>instanceof</code> works is it looks at the prototype property of the class' constructor and compares it to the object's prototype (__proto__). If they are the same then the object is the instance of the class</p>
<img src="./images/instanceof1.JPG" width="800" style="border:1px solid black">
<h2>8. Future directions</h2>
<p>The <code>class</code> syntax (new in ES6):</p>
<img src="./images/future-directions1.JPG" width="800" style="border:1px solid black">
<p>Side-by-side comparison with classical model:</p>
<img src="./images/future-directions2.JPG" width="800" style="border:1px solid black">