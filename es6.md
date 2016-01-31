##### let

ES6

	let message = "hi";
	{
		let message = "bye";
	}
	console.log(message); //hi

ES5

	var message = "hi";
	{
		var message = "bye";
	}
	console.log(message); //bye

ES5 has function scoping and not block scoping. With let, every block has a scope and it doesn't have to be just a function.

___

##### Arrow function style

ES5

	var createGreeting = function(msg, name) {
		return msg + name;
	}

ES6

		var createGreeting = (msg, name) => msg + name;

ES5

	var deliveryBoy = {
	name: "Doe",
	handleMsg: function(msg, handler) {
		handler(msg);
	},
	receive: function() {
		//console.log(this); gives the object
		var that = this;
		this.handleMsg("Hello", function(msg) {
			console.log(msg + that.name); //"this" loses its context here, that's why we've saved it in "that"
		})
	}
	}

	deliveryBoy.receive();

ES6

	var deliveryBoy = {
	name: "Doe",
	handleMsg: function(msg, handler) {
		handler(msg);
	},
	receive: function() {
		this.handleMsg("Hello", msg =>
			console.log(msg + this.name); //"this" doesn't refer to inside the function scope, rather refers to the scope outside - i.e: receive
		)
	}
	}

	deliveryBoy.receive();

___

##### Destructuring

	var {firstName, lastName} = {
		firstName: "Su",
		lastName: "Pai",
		place: "Atlanta",
		studies: "Gatech"
	}
	console.log(firstName + lastName); //Su Pai

{key, key} structure basically extracts the mentioned key values only from the object.

[https://gist.github.com/mikaelbr/9900818]

___

ES6 allows you to put the variables inside a string.
The template for it is - ${variableName}

___

##### Shorthands

	let firtname = "su";
	let lastname = "pai";
	let person = {firstname, lastname};
	console.log(person);// {firsname: 'su', lastname: 'pai'};
	let age = 24;
	let updatedPerson = {person, age};
	console.log(updatedPerson); // {person" {firstname: 'su', lastname: 'pai'}, age: 24}

___
##### Spread operator

This allows us to take an array and spread it out into its individual elements.

	console.log([1,2,3]); //[1,2,3];
	console.log(...[1,2,3]); //1 2 3

This also allows us to push elements into an array

	let first = [1,2,3];
	let second = [4,5,6];
	let ex1 = first.push(second); //[1,2,3, [4,5,6]];
	console.log(ex1); //[1,2,3, [4,5,6]];
	let ex2 = first.push(...second);
	console.log(ex2); //[1,2,3,4,5,6];
	console
