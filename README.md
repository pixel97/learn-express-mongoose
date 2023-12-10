# Express Basics

Run `$ npm install` before starting.

Run the file "basics/server1.js" and answer the following questions:

1. Identify the endpoint method in the code. Which phase of the event loop will the endpoint be scheduled to run?

Answer: 
> The endpoint method here is "GET".
>  It will be scheduled to run in the "poll" phase of the Node.js event loop

2. What do you see when you render "http://localhost:3001/" in the browser?

Answer:
> {"ping":"pong"}

3. Try console logging req.body inside the endpoint’s handler? What do you see in the console? Why?

Answer:
> undefined
> This is because the Express application hasn't been configured to parse the body of incoming requests, which is necessary for req.body to contain the parsed data.

In Express, req.body is populated by middleware that parses the body of incoming requests

JSON Middleware: For parsing JSON payloads.

app.use(express.json());


Open the file "basics/server2.js" and answer the following:

1. Run the server and list the order in which app.use and app.get functions are executed.

Answer:
> Console Output:
app listening on 3001
{}
{}
hello

2. Move app.use in line 20 to above the app.get endpoint. Run the server and list the order of execution.

Answer:
> Console Output:
app listening on 3001
{}
hello
{}
hello


3. Move all app.use functions above the app.get endpoint. Replace the return in the last app.use with next(). What will be the order of execution?

Answer:
> Console Output:
app listening on 3001
{}
hello
{}
hello

Open the file "basics/server3.js" and answer the following:

1. What are the *params* in the path?

Answer:
Params will be
userId
bookId

2. Assume the server is running on localhost:3002. Provide a path which would be handled by the endpoint shown and provide the output.

Answer:
localhost:3002//users/123/books/456
Output 
{ "p1": "123", "p2": "456" }

localhost:3002/user
localhost:3002/user?name=John&age=30 (with query params)
Output
{ "name": "John", "age": "30" }


3. Construct a URL with inputs for the end point defined in '/user'. 
localhost:3002/user?name=John&age=30

# Mongoose Basics

Open the file "basics/breakfastSchema.js". Inspect the schema structure and understand its meaning. Answer the following:

1. Run the schema and make sure there are no error.

2. What will happen if we create an instance of the schema with eggs set to 13?

Answer:
Attempting to create an instance of the BreakFastSchema with eggs set to 13 will result in a validation error due to the violation of the max constraint defined in the schema.

3. What will happen if we create an instance of the schema with drink set to "Milk"?

Answer:
Attempting to create an instance of the BreakFastSchema with drink set to "Milk" will result in a validation error due to the value not being part of the enumerated set defined in the schema.

4. Run "basics/mongoose-demo.js" and see what you get? make the changes in 2 and 3 and run again.

Output
Created Entry : [object Object]

With the changes 2 and 3
Output:

Failed : ValidationError: eggs: Path `eggs` (13) is more than maximum allowed value (12)., drink: `Milk` is not a valid enum value for path `drink`.

5. Define a function insertMany(entries) in the above script, which takes a list of objects {eggs: N, drink: ‘some drink’} and inserts each entry in entries in the MongoDB collection my_db.



# The Library App

We will make a library app to query information about books and create new books.

# References

1. https://mongoosejs.com/docs/index.html
2. https://mongoosejs.com/docs/guides.html
3. https://www.mongodb.com/basics 
4. https://expressjs.com/en/guide/writing-middleware.html
5. https://expressjs.com/en/guide/using-middleware.html
6. https://expressjs.com/en/guide/routing.html
