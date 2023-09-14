**Unit-1: PHP fundamentals
1.1 Concepts of Php and introduction
1.2 Php syntax: variables, constants, echo and print commands
1.3 Data types
1.4 Operators, Conditional Statements (if. Else, Switch. Case), Arrays
1.5 Sorting Arrays, Php Loops**

**1.1 Concepts of PHP and Introduction:**
   - PHP (Hypertext Preprocessor) is a server-side scripting language.
   - It is widely used for web development to create dynamic web pages.
   - PHP code is executed on the server, and the result is sent to the client's browser.

**1.2 PHP Syntax: Variables, Constants, Echo, and Print Commands:**
   - Variables: Used to store data. They start with a dollar sign ($) followed by a name.
   
   ```php
   $name = "John";
   ```

   - Constants: Values that do not change during script execution.
   
   ```php
   define("PI", 3.14159);
   ```

   - Echo and Print: Used to display output.
   
   ```php
   echo "Hello, World!";
   print("Welcome to PHP!");
   ```

**1.3 Data Types:**
   - PHP supports various data types, including integers, floats, strings, booleans, arrays, and more.

   ```php
   $num = 10; // Integer
   $price = 19.99; // Float
   $name = "Alice"; // String
   $is_active = true; // Boolean
   ```

**1.4 Operators, Conditional Statements, Arrays:**
   - Operators: Used for arithmetic, comparison, and logical operations.

   ```php
   $result = 5 + 3; // Addition
   $is_equal = ($result == 8); // Comparison
   $is_valid = true && false; // Logical
   ```

   - Conditional Statements (if, else, switch, case): Used for decision-making.

   ```php
   if ($age < 18) {
       echo "You are a minor.";
   } else {
       echo "You are an adult.";
   }

   switch ($day) {
       case "Monday":
           echo "It's Monday.";
           break;
       case "Tuesday":
           echo "It's Tuesday.";
           break;
       default:
           echo "It's another day.";
   }
   ```

   - Arrays: Used to store multiple values in a single variable.

   ```php
   $fruits = array("apple", "banana", "cherry");
   echo $fruits[0]; // Outputs "apple"
   ```

**1.5 Sorting Arrays, PHP Loops:**
   - Sorting Arrays: You can sort arrays in ascending or descending order.

   ```php
   $numbers = array(3, 1, 2, 4);
   sort($numbers); // Sort in ascending order
   ```

   - PHP Loops (for, while, foreach): Used for repetitive tasks.

   ```php
   for ($i = 0; $i < 5; $i++) {
       echo $i;
   }

   $count = 0;
   while ($count < 3) {
       echo "Count: " . $count;
       $count++;
   }

   $colors = array("red", "green", "blue");
   foreach ($colors as $color) {
       echo $color;
   }
   ```

**Unit-2: PHP functions
2.1 Math functions, Date and Time functions, GET and POST methods
2.2 Files: include, file parsing, directories, file upload, file download
2.3 Cookies and Sessions, Send Email
2.4 Forms: creating, handling, validation of forms, Php filters, Json parsing
2.5 Classes and objects in Php
2.6 Regular expressions and exception handling**


**2.1 Math Functions:**
PHP provides various math functions for performing mathematical operations. Here are some common math functions:

- `abs()`: Returns the absolute value of a number.

Example:
```php
$number = -5;
$absolute = abs($number); // $absolute is now 5
```

- `sqrt()`: Returns the square root of a number.

Example:
```php
$number = 25;
$squareRoot = sqrt($number); // $squareRoot is now 5
```

- `rand()`: Generates a random number.

Example:
```php
$randomNumber = rand(1, 100); // Generates a random number between 1 and 100
```

**Date and Time Functions:**
PHP offers functions to work with dates and times. Here are some examples:

- `date()`: Formats the current date and time.

Example:
```php
$currentDate = date("Y-m-d H:i:s"); // Current date and time in YYYY-MM-DD HH:MM:SS format
```

**GET and POST Methods:**
HTTP GET and POST methods are used to collect data from web forms.

- `$_GET[]`: Retrieves data sent to the server using the GET method.

Example:
```php
$param = $_GET['parameter_name']; // Retrieves the value of 'parameter_name' from the URL
```

- `$_POST[]`: Retrieves data sent to the server using the POST method.

Example:
```php
$value = $_POST['input_field_name']; // Retrieves the value of 'input_field_name' from a form submission
```

**2.2 Files: Include, File Parsing, Directories, File Upload, File Download:**

**Include:**
- PHP provides `include` and `require` statements to include external PHP files into your script.

Example of `include`:
```php
include 'header.php'; // Includes the contents of 'header.php' into the current script
```

Example of `require`:
```php
require 'functions.php'; // Requires 'functions.php' to be included; it will produce a fatal error if the file is not found
```

**File Parsing:**
- You can read and manipulate files in PHP using functions like `fopen`, `fread`, `fwrite`, etc.

Example of reading a file:
```php
$filename = "sample.txt";
$file = fopen($filename, "r"); // Opens the file for reading

if ($file) {
    while (($line = fgets($file)) !== false) {
        echo $line; // Outputs each line from the file
    }
    fclose($file); // Closes the file
} else {
    echo "Failed to open the file.";
}
```

**Directories:**
- PHP offers functions for working with directories, such as `mkdir`, `rmdir`, `scandir`, and `chdir`.

Example of creating a directory:
```php
$directoryName = "new_directory";
if (!is_dir($directoryName)) {
    mkdir($directoryName); // Creates a new directory if it doesn't exist
    echo "Directory created successfully.";
} else {
    echo "Directory already exists.";
}
```

**File Upload:**
- You can handle file uploads from HTML forms in PHP using the `$_FILES` superglobal.

Example of handling file upload:
```php
$targetDir = "uploads/";
$targetFile = $targetDir . basename($_FILES["fileToUpload"]["name"]);

if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $targetFile)) {
    echo "File is valid and uploaded successfully.";
} else {
    echo "File upload failed.";
}
```

**File Download:**
- You can enable file downloads in PHP by setting appropriate headers.

Example of triggering a file download:
```php
$filePath = "files/sample.pdf";
if (file_exists($filePath)) {
    header('Content-Description: File Transfer');
    header('Content-Type: application/octet-stream');
    header('Content-Disposition: attachment; filename="'.basename($filePath).'"');
    header('Expires: 0');
    header('Cache-Control: must-revalidate');
    header('Pragma: public');
    header('Content-Length: ' . filesize($filePath));
    readfile($filePath);
} else {
    echo "File not found.";
}
```

**2.3 Cookies and Sessions:**

**Cookies:**
- Cookies are small pieces of data stored on a user's computer. They can be used to store user-specific information.

Example of setting a cookie:
```php
$cookieName = "user";
$cookieValue = "John";
$expiry = time() + 3600; // Expires in one hour
setcookie($cookieName, $cookieValue, $expiry, "/");
```

Example of retrieving a cookie:
```php
if (isset($_COOKIE["user"])) {
    $username = $_COOKIE["user"];
    echo "Welcome back, $username!";
} else {
    echo "No cookie found.";
}
```

**Sessions:**
- Sessions allow you to store user-specific data on the server.

Example of starting a session:
```php
session_start();
$_SESSION["username"] = "Alice";
```

Example of retrieving session data:
```php
session_start();
if (isset($_SESSION["username"])) {
    $username = $_SESSION["username"];
    echo "Hello, $username!";
} else {
    echo "Session data not found.";
}
```

**Send Email:**

**Sending Email:**
- PHP's `mail` function allows you to send emails.

Example of sending an email:
```php
$to = "recipient@example.com";
$subject = "Hello";
$message = "This is a test message.";
$headers = "From: sender@example.com";
mail($to, $subject, $message, $headers);
```


**2.4 Forms: Creating, Handling, Validation of Forms, PHP Filters, JSON Parsing:**

**Creating Forms:**
- HTML forms are essential for user input in web applications. PHP can process form data.

Example of creating a simple form:
```html
<form method="post" action="process.php">
    <input type="text" name="username" placeholder="Username">
    <input type="password" name="password" placeholder="Password">
    <button type="submit">Submit</button>
</form>
```

**Handling Form Data:**
- PHP can process form data using the `$_POST` or `$_GET` superglobals.

Example of handling form data with `$_POST`:
```php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $username = $_POST["username"];
    $password = $_POST["password"];
    // Process the data here
}
```

**Form Validation:**
- You can validate user input to ensure it meets certain criteria.

Example of validating an email address:
```php
$email = $_POST["email"];
if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    $error = "Invalid email format";
}
```

**JSON Parsing:**
- JSON (JavaScript Object Notation) is a common data format used in web applications.

Example of parsing JSON data in PHP:
```php
$jsonData = '{"name": "John", "age": 30, "city": "New York"}';
$data = json_decode($jsonData);
echo "Name: " . $data->name . ", Age: " . $data->age . ", City: " . $data->city;
```



**2.5 Classes and Objects in PHP:**

**Defining a Class:**
- A class is a blueprint for creating objects. It defines properties (variables) and methods (functions) that the objects of the class will have.

Example of defining a class:
```php
class Car {
    public $brand;
    public $model;

    function start() {
        echo "The car is starting.";
    }

    function stop() {
        echo "The car is stopping.";
    }
}
```

**Creating Objects:**
- Once a class is defined, you can create objects (instances) of that class.

Example of creating an object:
```php
$myCar = new Car();
$myCar->brand = "Toyota";
$myCar->model = "Camry";
```

**Accessing Properties and Methods:**
- You can access the properties and methods of an object using the arrow (`->`) notation.

Example of accessing properties and methods:
```php
echo "Brand: " . $myCar->brand; // Outputs "Brand: Toyota"
$myCar->start(); // Outputs "The car is starting."
```

**Constructor and Destructor:**
- A constructor is a special method called when an object is created, and a destructor is called when an object is destroyed.

Example of a constructor and destructor:
```php
class MyClass {
    function __construct() {
        echo "Object created.";
    }

    function __destruct() {
        echo "Object destroyed.";
    }
}
```

**Inheritance:**
- Inheritance allows you to create a new class that inherits properties and methods from an existing class.

Example of inheritance:
```php
class Animal {
    public $name;

    function __construct($name) {
        $this->name = $name;
    }

    function speak() {
        echo "$this->name is speaking.";
    }
}

class Dog extends Animal {
    function bark() {
        echo "$this->name is barking.";
    }
}
```

**2.6 Regular Expressions and Exception Handling:**

**Regular Expressions:**
- Regular expressions (regex) are powerful patterns used for string matching and manipulation.

Example of using regex to validate an email address:
```php
$email = "user@example.com";
if (preg_match("/^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/", $email)) {
    echo "Valid email address.";
} else {
    echo "Invalid email address.";
}
```

**Exception Handling:**
- Exception handling allows you to gracefully handle errors and exceptions in your code.

Example of using try-catch for exception handling:
```php
try {
    $result = 10 / 0; // This will throw a DivisionByZeroError
} catch (DivisionByZeroError $e) {
    echo "Division by zero error: " . $e->getMessage();
} catch (Exception $e) {
    echo "An error occurred: " . $e->getMessage();
}
```

**Custom Exceptions:**
- You can create custom exception classes to handle specific situations.

Example of a custom exception class:
```php
class MyCustomException extends Exception {
    public function errorMessage() {
        return "Custom Exception: " . $this->getMessage();
    }
}

try {
    throw new MyCustomException("This is a custom exception.");
} catch (MyCustomException $e) {
    echo $e->errorMessage();
}
```
