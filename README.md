# C# vs. .NET

- C# is programming Language
- .NET is a framework for building applications on windows
- CLR(Command Language Runtime)
- Class Library

# CLR

Common Language Runtime is essentially an application sitting in the memory whose job is to translate the code into the machine code, and this process is called Just In Time compiler action or JIT.

# Architecture of .NET Applications

In terms of architecture, an application written with C# consists of building blocks called classes. A class is a container for data (attributes) and methods (functions). Attributes represent the state of the application. Methods include code. They have logic. That's where we implement our algorithms and write code.

A namespace is a container for related classes. So as your application grows in size, you may want to group the related classes into various namespaces for better maintainability.

As the number of classes and namespaces even grow further, you may want to physically separate related namespaces into separate assemblies. An assembly is a file (DLL or EXE) that contains one or more namespaces and classes. An EXE file represents a program that can be executed. A DLL is a file that includes code that can be re-used across different programs.

# Overflowing

To stop the overflowing of the data space we should use checked keyword, "checked" keyword will throw an exception at the runtime and the application will get crashed until the exception is handled.

```csharp

checked {
	byte number = 255; // as byte only have the storage range till 255
	number = number + 1; // we do add one it will overflow to avoid this we are using checked
}

```

# Type Conversion

- Implicit type conversion
- Explicit type conversion(casting)
- Conversion between non-compatible types

### 1. Implicit type conversion:

```csharp
byte b = 1;
int i = b;
```

### 2. Explicit type Conversion

```csharp
float f = 1.0f;
int i = (int)f; //loss of data will happen
```

### 3. Non-compatible type

```csharp
string s = "1";
int i = Convert.ToInt32(s);
int j = int.Parse(s);
```

# The Basics: Hello World

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

# Variable and Data Types

For creating any variable in C# we use "var" keyword,

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            var a = "My name is Sanskar Gupta";
            var b = 21;
            Console.WriteLine(a);
            Console.WriteLine("and my age is: " + b);
        }
    }
}
```

**Convert→**

- ToByte() to convert the type into byte
- ToInt16() to convert the type into short
- ToInt32() to convert the type into integer
- ToInt64() to convert the type into Long

# Input

To read input from the user we use Console.ReadLine(),

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            var a = Console.ReadLine();
            Console.WriteLine(a);
           
        }
    }
}
```

# Conditional Statements with While loop

Using the while loop with the Conditional statements,

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            var passcode = "secret";
            var userPasscode = "";

            while(userPasscode != passcode)
            {
                Console.WriteLine("Enter a passcode: ");
                userPasscode = Console.ReadLine();

                if (userPasscode == passcode)
                {
                    Console.WriteLine("You're succesfully authenticated!");

                }
                else
                {
                    Console.WriteLine("Authentication failed!");
                }
            }
            
        }
    }
}
```

# Date and Time in C#

To work with Date and Time object in C# we use system library which contains this object

```csharp
var dateTime = new DateTime(2021, 7, 5);

var now = DateTime.Now;
var today = DateTime.Today;

var tomorrow = now.AddDays(1);
var yesterday = now.AddDays(-1);

// to covert DateTime object into string,

Console.WriteLine(now.ToLongDateString());
Console.WriteLine(now.ToShortDateString());
Console.WriteLine(now.ToLongTimeString());
Console.WriteLine(now.ToShortTimeString());
Console.WriteLine(now.ToString());
```

There is also TimeSpan Object which is present in C#,

```csharp
var timeSpan = new TimeSpan(1, 20, 30);

var timeSpan1 = TimeSpan.FromHours(1);

var start = DateTime.Now;
var end = DateTime.Now.AddMinutes(2);
var duration = end - start;
Console.WriteLine("Duration: " + duration);

//Properties
Console.WriteLine("Minutes: " + timeSpan.Minutes);
Console.WriteLine("Minutes: " + timeSpan.TotalMinutes);

//Add
Console.WriteLine("Add Example: " + timeSpan.Add(TimeSpan.FromMinutes(10)));
Console.WriteLine("Subtract Example: " + timeSpan.Subtract(TimeSpan.FromMinutes(5)));

//ToString
Console.WriteLine("ToString" + timeSpan.ToString());

//Parse > another way of converting a timespan to string
Console.WriteLine("Parse" + TimeSpan.Parse("01:10:20"));
```

# Working with Files

In .NET we have a namespace called System.IO, which contains many of useful classes which can be helpful to work with the Files, in C#. Some of them are,

 

- File, FileInfo: Provides methods for creating, copying, deleting, moving and opening files.

    FileInfo: provides instance methods,

    File: provides static methods,

    Some method of this class are,

    1. Create()
    2. Copy()
    3. Delete()
    4. Exists()
    5. GetAttributes()
    6. Move()
    7. ReadAllText()

- Directory, DirectoryInfo: They are very similar to the File, and FileInfo

    Directory: provides static methods

    DirectoryInfo: provides instance methods

    Some useful methods of this class are,

    1. CreateDirectory()
    2. Delete()
    3. Exists()
    4. GetCurrentDirectory()
    5. GetFiles()
    6. Move()
    7. GetLogicalDrives() → return the logical drive of the system e.g, C Drive, D Drive

- Path: To work with the string or directory path information, some useful methods of the this class are,
    1. GetDirectoryName()
    2. GetFileName()
    3. GetExtension()
    4. GetTempPath()

# Arrays

Represents a fixed number of variables of a particular type.

For creating the array we can use new int[] {no. of items in array};

```csharp
using System;

namespace Arrays1
{
    class Program
    {
        static void Main(string[] args)
        {
            var studentGrades = new int[]{ 1, 2, 3, 4, 5, 6, 7 ,8, 9, 10};
            var len = studentGrades.Length;
            Console.WriteLine(len);
            Console.WriteLine(studentGrades[5]);
        }
    }
}
```

There are two types of arrays in C#:

- Single Dimensional Arrays
- Multi-Dimensional Arrays(2D)
    - Rectangular Arrays

        ```csharp
        var matrix = new int[3, 5]
        var matrix = new int[3, 5]
        {
        	{1, 2, 3, 4, 5},
        	{1, 22, 35, 4, 5},
        	{1, 22, 3, 45, 5},
        };

        // for accessing this array
        var element = matrix[0,0];
        ```

    - Jagged Arrays

        ```csharp
        var matrix = new int[3][];
        array[0] = new int[4];
        array[1] = new int[5];
        array[2] = new int[3];

        // for accessing this type of array
        array[0][0] = 1;
        ```

        ### Array's method:

        - Clear()
        - Copy()
        - IndexOf()
        - Reverse()
        - Sort()

# Strings

String is a Reference type variable which used very commonly and mostly all on the cases.

There are some important methods of string,

- Trim()
- ToUpper()
- ToLower()
- Substring()
- Split()
- Replace()
- IsNullOrWhiteSpace()

these all method are implemented in the code block below,

```csharp
var fullName = "Sanskar Gupta    ";
Console.WriteLine($"Trim: '{fullName.Trim()}'");
Console.WriteLine($"Trim: '{fullName.Trim().ToUpper()}'");
Console.WriteLine($"Trim: '{fullName.Trim().ToLower()}'");

var idx = fullName.IndexOf(' ');
var FirstName = fullName.Substring(0, idx);
var LastName = fullName.Substring(idx + 1);
Console.WriteLine("First Name: "+FirstName);
Console.WriteLine("Last Name: "+LastName);

var names = fullName.Split(' ');
Console.WriteLine("First Name: "+names[0]);
Console.WriteLine("Last Name: "+names[1]);

Console.WriteLine(fullName.Replace("Sanskar", "My name is Sanskar"));
Console.WriteLine(fullName);

if (string.IsNullOrWhiteSpace(" " ))
{
    Console.WriteLine("invalid");
}
```

## Creating Strings

```csharp
var numbers = new int[3] {1, 2, 3};
string list = string.Join("," , numbers);
```

## Verbatim Strings

Verbatim pattern can be use to implement backslashes or any special characters between the strings

```csharp
string path = "c:\\projects\\project1\\folder1";
string path = @"c:\projects\project1\folder1"; // this verbatim pattern can be use to implement backslashes or any special characters between the strings.

```

## Displaying Array elements using For-Each Loop:

```csharp
using System;

namespace Arrays1
{
    class Program
    {
        static void Main(string[] args)
        {
            var studentGrades = new int[]{ 1, 2, 3, 4, 5, 6, 7 ,8, 9, 10};
            foreach (var studentGrade in studentGrades)
            {
                Console.WriteLine(studentGrade);
            }
            
        }
    }
}
```

## String Builder

StringBuilder is a class in C# which is used to easy manipulation of the string, but it is not for performing the search operations,

Some methods of String Builder are,

- Append()
- Remove()
- Replace()
- Insert()
- Equals()

```csharp
var builder1 = new StringBuilder();
builder1.Append('-', 10);
builder1.AppendLine();
builder1.Append("Header");
builder1.AppendLine();
builder1.Append('-', 10);

builder1.Replace('-', '+');

builder1.Remove(0, 10);
builder1.Insert(0, new string('+', 10));

Console.WriteLine(builder1);

var builder2 = new String("Sanskar");

if(builder1.Equals(builder2))
{
	Console.WriteLine("Yes");
}
```

# Functions With Return Type

```csharp
using System;

namespace GettingInfo
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Enter Your name: ");
            var name = Console.ReadLine();
            
            if(name == "")
            {
                name = TryAgain();
            }

            Console.WriteLine("Your name is: {0}", name);  
        }

        static string TryAgain()
        {
            Console.WriteLine("Yoy have not typed any name, please try again");
            return Console.ReadLine();
        }
    }

}
```

```csharp
using System;

namespace GettingInfo
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Enter Your name: ");
            var name = TryAnswer();

            Console.WriteLine("Enter Your age: ");
            var age = TryAnswer();

            Console.WriteLine("Enter Your month: ");
            var month = TryAnswer();

            Console.WriteLine("Your name is: {0}", name);  
            Console.WriteLine("Your age is: {0}", age);  
            Console.WriteLine("Your month is: {0}", month);
        }

        static string TryAnswer()
        {
            var question = Console.ReadLine();
            if(question == "")
            {
                Console.WriteLine("Yoy have not typed any name, please try again");
                return Console.ReadLine();
            }

            return question;
        }
    }

}
```

**Note**: To convert string input to integer input use,

```csharp
int.Parse(Console.ReadLine());
```

# Switch Statement:

```csharp
using System;

namespace JobCandidate
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("How many years of experience do you have?");
            var years = int.Parse(Console.ReadLine());

            switch(years)
            {
                case 0:
                    Console.WriteLine("Inexperienced");
                    break;

                case 1:
                    Console.WriteLine("Junior");
                    break;

                case 2:
                    Console.WriteLine("Intermediate");
                    break;

                case 3:
                    Console.WriteLine("Advanced");
                    break;

                default:
                    Console.WriteLine("Senior");
                    break;
            }
        }
    }
}
```

# Dynamic Arrays Implementation

```csharp
using System;

namespace Arrays1
{
    class Program
    {
        static void Main(string[] args)
        {

            Console.WriteLine("How many Students there in the class? ");
            var studentCount = int.Parse(Console.ReadLine());
            var studentNames = new string[studentCount];
            var studentGrades = new int[studentCount];

            for (int i = 0; i < studentCount; i++)
            {
                Console.WriteLine("Student Name: ");
                studentNames[i] = Console.ReadLine();

                Console.WriteLine("Student Grades: ");
                studentGrades[i] = int.Parse(Console.ReadLine());
            }

            for (int i = 0; i < studentCount; i++)
            {
                Console.WriteLine("Name: {0}, Grades: {1}", studentNames[i], studentGrades[i]);
            }

        }
    }
}
```

# Collections(List) in C#

List is more dynamic than the Array, we can add any amount of item at any stage in the program, to import list in your use → "**using System.Collection.Generic**",

```csharp
using System;
using System.Collections.Generic; // for importing the Collection Class

namespace Arrays1
{
    class Program
    {
        static void Main(string[] args)
        {

            var studentNames = new List<string>();
            var studentGrades = new List<int>();
            var adding = true;

            while(adding)
            {
                Console.WriteLine("Student Name: ");
                studentNames.Add(Console.ReadLine());

                Console.WriteLine("Student Grades: ");
                studentGrades.Add(int.Parse(Console.ReadLine()));

                Console.WriteLine("Add another? y/n");
                if (Console.ReadLine() != "y")
                {
                    adding = false;
                }
            }

            for (int i = 0; i < studentNames.Count; i++)
            {
                Console.WriteLine("Name: {0}, Grades: {1}", studentNames[i], studentGrades[i]);
            }

        }
    }
}
```

### Useful Methods of List:

- Add()
- AddRange()

    ```csharp
    var numbers = new List<int>() { 1, 2, 3, 4 };
    numbers.AddRange(new int[3] { 5, 6, 7 };
    foreach (var number in numbers)
    {
        Console.WriteLine(number);
    }
    ```

- Remove()
- RemoveAt()
- IndexOf()
- Contains()
- Count : this is the property of the List Class

# OOP in C#

## 1. Class

```csharp
using System;
using System.Collections.Generic;

namespace StudentTracker
{
    class Program
    {
        static void Main(string[] args)
        {

            var students = new List<Student>();

            var adding = true;

            while (adding)
            {
                var newStudent = new Student();
                Console.WriteLine("Student Name: ");
                newStudent.Name = Console.ReadLine();

                Console.WriteLine("Student Grades: ");
                newStudent.Grades = int.Parse(Console.ReadLine());

                students.Add(newStudent);

                Console.WriteLine("Add another? y/n");
                if (Console.ReadLine() != "y")
                {
                    adding = false;
                }
            }

            foreach (var student in students)
            {
                Console.WriteLine("Name: {0}, Grades: {1}", student.Name, student.Grades);
            }

        }
    }

    class Student
    {
        public string Name;
        public int Grades;
        public int Birthday;
        public string Address;
        public string Phone;
    }
}
```

### Class Members:

- Instance: accessible from an object

    ```csharp
    var person = new Person();
    person.Introduce();
    ```

- Static; accessible from the class

    ```csharp
    Console.WriteLine();
    ```

### The Params Modifier

This modifier is used when we have to take multiple inputs in one time from the user,

```csharp
public class Calculator {
	 public int Add(params int[] numbers) {
			var sum = 0;
			foreach(var number in numbers) {
				sum+=number;
			}
			return sum;
	}
}

var result = calculator.Add(new int[] {1, 2, 4, 5}); // instead doing this,
var result = calculator.Add(1, 2, 4, 5); // we can do this!
```

### The Ref Modifier

This modifier helps the code to pass value type variables as reference to the function so as to modify its value of the original variable

```csharp
public clas Weirdo {
	public void DoAWeirdThing(ref int a) {
		a += 2; // ref can help to modify the original var a;
	}
}
var a = 1;
weirdo.DoAWeirdThing(ref a);
```

### The Out Modifier

This type of modifier can help the caller to get the multiple return values at a single time, though this is not good practice to use out modifier while writing C# code, there are some cases in .NET framework where we have use this modifier.

```csharp
public class MyClass
{
	public void MyMethod(out int result) {
		result = 1;
	}
}
int a;
myClass.MyMethod(out a);
```

### ReadOnly Modifier

If you want to initialize any field only once for any instance then you can use readonly modifier. It can be a way to improve the robustness in the application.

```csharp
public class Customer {
	public int id;
	public readonly List<Order> Orders = new List<Order>();
	
	public Customer(int id)
	{
		this.Id = id;
	}
}
```

### The Access Modifiers

This is an type of security level you provide to your application components like its class, fields, methods. Basically, these are a way to control access to a class and/or its members. There are different types of access modifiers in C#,

- Public
- Private
- Protected
- Internal
- Protected Internal

1. **Public Modifier**: ****Accessible from everywhere
2. **Private**: Accessible only from the class. 
3. **Protected**: Accessible only from the class and its derived class (it is not recommended to use protected method much, because our main focus is always to hide the internal implementation details, protected modifier breaks this rule, which can be very tedious to solve after).
4. **Internal**: Accessible only from the same assembly. This class is used when we have more than one assembly and we have to define some internals of assembly classes which should only be visible to that same assembly then we can use Internal Modifier, to make the class visible throughout the same assembly and not the other.
5. **Protected Internal**: It is a mix of Internal and Protected modifier.

## 2. Encapsulation

It is Used to Contain methods and fields into a single unit to make application more secure with hiding details and restricting the direct access of the fields of any class in an application. Two things to do make the encapsulation possible, 

- Define fields as private
- Provide getter/setter methods as public

**Note:** While implementing Encapsulation remember Classes, properties and methods they all use **PascalCase** for naming conventions, the only term in which we use **camelCase** is with private fields and method parameters, we use this technique to improve our application security and robustness.

```csharp
using System;
using System.Collections.Generic;

namespace StudentTracker
{
    class Program
    {
        static void Main(string[] args)
        {

            var students = new List<Student>();

            var adding = true;

            while (adding)
            {
                var newStudent = new Student();
                Console.WriteLine("Student Name: ");
                newStudent.SetName(Console.ReadLine());

                Console.WriteLine("Student Grades: ");
                newStudent.Grades = int.Parse(Console.ReadLine());

                students.Add(newStudent);

                Console.WriteLine("Add another? y/n");
                if (Console.ReadLine() != "y")
                {
                    adding = false;
                }
            }

            foreach (var student in students)
            {
                Console.WriteLine("Name: {0}, Grades: {1}", student.GetName(), student.GetGrades());
            }

        }
    }

    class Student
    {
        private string name;
        private int grades;
        private int Birthday;
        private string Address;
        private string Phone;

				// this is the C# property
        public int Grades
        {
            set { grades = value; }
        }

        public void SetName(string name)
        {
            this.name = name;
        }

        public string GetName()
        {
            return name;
        }

        public void SetGrades(int grades)
        {
            this.grades = grades;

        }

        public int GetGrades()
        {
            return grades;
        }
    }
}
```

### Properties:

A class member that encapsulates a getter/setter for accessing a field. It is widely used to create a getter/setter with less code in C#.

```csharp
public class Person {
	// we used camelCase for field(_birthDate) here
	private DateTime _birthDate; 

	// this is the property	 
	public DateTime BirthDate {
		get {return _birthDate; }
		set {_birthDate = value; }
	}
```

There is also Auto-Implemented Properties which can be use to reduce the code. If you don’t need to write any specific logic in the get or set method, it’s more efficient to create an auto-implemented property. An auto-implemented property encapsulates a private field behind the scene. So you don’t need to manually create one. The compiler creates one for you:

```csharp
public class Person {
	// this is the Auto-Implemented property	 
	public DateTime BirthDate {get, set;} // now C# by itself will create a private field 
																						// of _birthDate for you and also the getter and setter methods
```

To explain this concept of properties, I have created a simple example, given below

```csharp
using System;

namespace CSharpPropertiesExercise
{
    class Program
    {
        static void Main(string[] args)
        {
            var person1 = new Person();
            person1.BirthDate = new DateTime(1995, 08, 03);
            Console.WriteLine(person1.BirthDate);
            Console.WriteLine(person1.Age);
        }
    }
}
```

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace CSharpPropertiesExercise
{
    class Person
    {
					
        public DateTime BirthDate { get; set; }
					
        public int Age
        {
            // here I have not created any set method as it is intentional,
            // because setting someones age is a bad idea when we have his DOB.
            get
            {
                var timeSpan = DateTime.Today - BirthDate;
                var years = timeSpan.Days / 365;
                return years;
            }
        }
    }
}
```

Now, here we can assume that we came up with the requirement that BirthDate of any person should be set once and will not be changed again, so to tackle this requirement what we do, we make our **set** method of BirthDate to private which will help us to set the BirthDate once,

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace CSharpPropertiesExercise
{
    class Person
    {
				// Auto-Implemented Property
        public DateTime BirthDate { get; private set; }

        public Person(DateTime _birthDate)
        {
            BirthDate = _birthDate;
        }
				
				// Property
        public int Age
        {
            // here I have not created any set method as it is intentional,
            // because setting someones age is a bad idea when we have his DOB.
            get
            {
                var timeSpan = DateTime.Today - BirthDate;
                var years = timeSpan.Days / 365;
                return years;
            }
        }
    }
}
```

We have created constructor here because now we setting up the BirthDate only once when we are creating an instance of an Person class. Main method will also now get updated,

```csharp
using System;

namespace CSharpPropertiesExercise
{
    class Program
    {
        static void Main(string[] args)
        {
            var person1 = new Person(new DateTime(1995, 08, 03));
            //person1.BirthDate = new DateTime(2000, 07, 05); we will get error now in this line
            Console.WriteLine(person1.BirthDate);
            Console.WriteLine(person1.Age);
        }
    }
}
```

```csharp
using System;

namespace CSharpPropertiesExercise
{
    class Program
    {
        static void Main(string[] args)
        {
            var person1 = new Person(new DateTime(1995, 08, 03));
            //person1.BirthDate = new DateTime(2000, 07, 05); we will get error now in this line
            Console.WriteLine(person1.BirthDate);
            Console.WriteLine(person1.Age);
        }
    }
}
```

### Indexers

A way to access elements in a class that represents a list of values.

- Indexer is a special kind of property that allows accessing elements of a list by an index.
- If a class has the semantics of a list, or collection, we can define an indexer property for it. This way it’s easier to get or set items in the collection.

Example is given below,

```csharp
using System;

namespace CSharpIndexerExercise
{
    class Program
    {
        static void Main(string[] args)
        {
            var cookie = new HttpCookies();
            cookie["info"] = "Transaction Successful";
            Console.WriteLine(cookie["info"]);
        }
    }
}
```

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace CSharpIndexerExercise
{
    class HttpCookies
    {
        private readonly Dictionary<string, string> _dictionary;
        public HttpCookies()
        {
            _dictionary = new Dictionary<string, string>();
        }
					//indexer initialization
        public string this[string key]
        {
            get { return _dictionary[key]; }
            set { _dictionary[key] = value; }
        }
    }
}
```

## 3. Constructor

A method that is called when an instance of a class is created. It has the same name as of the class name. It do not have return type not even void. There are three types of Constructor,

- Default Constructor,
- Parameterized Constructor
- Copy Constructor

```csharp
using System;
using System.Collections.Generic;

namespace StudentTracker
{
    class Program
    {
        static void Main(string[] args)
        {
            Import();
            var students = new List<Student>();

            var adding = true;

            while (adding)
            {
                var newStudent = new Student();
                newStudent.SetName(Util.Console.Ask("Student Name: "));

                Console.WriteLine("Student Grades: ");
                newStudent.SetGrades(int.Parse(Util.Console.Ask("Student Name: ")));
                students.Add(newStudent);
                Student.count++;
                Console.WriteLine(Student.count);

                Console.WriteLine("Add another? y/n");
                if (Console.ReadLine() != "y")
                {
                    adding = false;
                }
            }

            foreach (var student in students)
            {
                Console.WriteLine("Name: {0}, Grades: {1}", student.GetName(), student.GetGrades());
            }

        }

        static void Import()
        {
            var importedStudent = new Student("Sanskar Gupta", 20);
            Console.WriteLine(importedStudent.GetName());
        }
    }

    class Student
    {
        static public int count = 0;
        private string name;
        private int grades;
        private int Birthday;
        private string Address;
        private string Phone;

		// Empty Constructor so to initialize Student object without parameters
        public Student()
        {

        }
        public Student(string name, int grades) 
        {
            this.name = name;
            this.grades = grades;
        }

        public int Grades
        {
            set { grades = value; }
        }

        public void SetName(string name)
        {
            this.name = name;

        }

        public string GetName()
        {
            return name;
        }

        public void SetGrades(int grades)
        {
            this.grades = grades;

        }
        public int GetGrades()
        {
            return grades;
        }
    }
}
```

### Constructor Overloading

Have method with the same but with different signatures(parameters)

```csharp
public class Customer {
	public Customer() {..}
	public Customer(string name) {...}
	public Customer(int cust_id, string name) {...}
```

If we want to use default constructor also, with other constructors as it may contain some important initialization we can use this keyword as shown below,

```csharp
public class Customer {
	public int Id;
	public string Name;
	public List<Order> Orders;

	public Customer() {
		Orders = new List<Orders>();
	}
	public Customer(string name) 
		// for accessing the default keyword
		:this() {
		this.id = id;
	}
	public Customer(string name) 
		:this(id)
	{
		this.Name = Name;
	}
}
```

### Object Initializers in C#

It is an another way to initialize an object. It is a syntax for quickly initializing an object without the need to call one of its constructors. We used this thing just avoid the use of multiple constructor. Example,

```csharp
var person = new Person
									{
										FirstName = "YourName",
										LastName = "YourLastName",
									};
```

## 4. Inheritance

- A kind of relationship between two classes that allows one to inherit code from other.
- Is-A
- Example: A Car is a Vehicle.

### Benefits:

- Code re-use
- Polymorphic behaviour

### Problems with Inheritence

- Easily abused by amateur designers/developers
- Large hierarchies
- Fragility
- Tightly Coupling

### Constructor in Inheritance

- Base class constructor are always executed first
- Base class constructor are not inherited

```csharp
public class Vehicle
{
	private string _registrationNumber;
	public Vehicle(string registrationNumber) {
		_registrationNumber = registrationNumber;
	}
}

public class Car : Vehicle
{
	public Car(string registrationNumber) {
		// below line will give an error
		_registrationNumber = registrationNumber;
	}
}
```

As I have mentioned in the above code that it will give error because **_registrationNumber** is defined private in the base class Vehicle so we cannot be able to access it in the derived class Car.

One way to solve this problem is to make **_registrationNumber** in base class protected but it will break the rule of encapsulation and our application will not be secured and reliable to use.

Another efficient way to solve this problem is to reuse the code of the base Class Vehicle, how can we do that? We can use **base** keyword to access the base class, below is the implementation,

```csharp
public class Car : Vehicle
{
	public Car(string registrationNumber)
					: base(registrationNumber)
 {
		// Initialise fields only specific to the Car Class, we don't have to
		// reassign the registrationNumber here again as it is not covered by
		// the base keyword.
	}
}
```

### Up-Casting/Down-Casting

- Conversion from a derived class to a base class is, UpCasting

    ```csharp
    // upcasting is an implicit type conversion
    Circle circle = new Circle();
    Shape shape = circle;
    ```

- Conversion from a base class to a derived class is, DownCasting

    ```csharp
    Circle circle = new Circle();
    Shape shape = circle;
    // we can convert shape to circle type using explicit conversion this is downcasting
    Circle anotherCircle = (Circle)shape;
    ```

    One thing to be cautious about the DownCasting that it can throw InvalidCastException. In the above downcasting code example our shape object is actually pointing to a circle object in runtime. So we can cast it to a circle but if we try to cast it to another type like a car it's going to throw an exception, like this,

    ```csharp
    Car car = (Car) shape; // throws InvalidCastException
    ```

    Now to prevent this from happening we can use the **as** keyword.

    So imagine we have an object and we would like to convert it to a car with explicit cast as you see here.

    ```csharp
    // now if the object cannot be converted to the target type we are not going to get an exception
    // instead what is return will be null.
    Car car = obj as Car;

    // so in the next line we can check if the result is not known. 
    if(car != null)
    {
    	...
    }
    ```

    We also have **is** key word with the key word we can check the type of an object.

    ```csharp
    if(obj is Car) 
    {
    	Car car = (Car) obj;
    	...
    }
    ```

    ### Why we use UpCasting?

    In C# UpCasting is implicit, so you can simply convert an object reference to its base class reference. In practical terms that means whenever a method requires an object of a given type you can pass an object of that type or any types that derives from that type(class). This is why we use UpCasting so that we can use any methods of the base class also.

    ### Why we use DownCasting?

    In C# DownCasting is explicit, so you can convert an object of base type reference to its derived class reference. In practical terms that means anywhere, where your method requires an argument and that argument gives a limited view to the object you can use downcasting to convert that object to a more specific type an to do that you can use an explicit cast or the **as** keyword.

    ### Boxing/Unboxing

    The process of converting a value type instance to an object reference is known as Boxing.

    ```csharp
    int number = 10;
    object obj = number;

    //or
    object obj = 10;
    ```

    Unboxing is just the opposite of Boxing, in which convert a reference type into a value type

    ```csharp
    object obj = 10;
    int number = (int)obj;
    ```

## 5. Composition

- A kind of relationship between two classes that allows one to contain the other
- Has-a relationship
- Example: Car has an Engine

### Benefits:

- Code re-use
- flexibility
- A means to loose-coupling

Example:

- DbMigrator requires logging
- Installer requires logging

```csharp
public class Logger
{
	public void Log(string message) 
	{
		Console.WriteLine(message);
	}
}
```

```csharp
public class DbMigrator 
{
	private readonly Logger _logger;

	public DbMigrator(Logger logger) {
		_logger = logger;
	}

	public void Migrate() {
		_logger.Log("We are Migrating!");
	}
}
```

```csharp
public class Installer
{
	private readonly Logger _logger;

	public Installer(Logger logger) {
		_logger = logger;
	}

	public void Install() {
		_logger.Log("We are Installing!");
	}
}
```

```csharp
class Program 
{
	static void Main(string[] args) {
		var dbMigrator = new DbMigrator(new Logger());
		
		var installer= new Installer(new Logger());

		dbMigrator.Migrate();
		installer.Install();
	}
}
```

## Working with namespaces

To create your own utility class for taking input and giving output at the same time we can create another file which can be named as Console.cs(purposely for this),

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace Util

{
    class Console
    {
        static public string Ask(string question)
        {
            System.Console.WriteLine(question);
            return System.Console.ReadLine();
        }
    }
}
```

```csharp
using System;
using System.Collections.Generic;

namespace StudentTracker
{
    class Program
    {
        static void Main(string[] args)
        {

            var students = new List<Student>();

            var adding = true;

            while (adding)
            {
                var newStudent = new Student();
                newStudent.SetName(Util.Console.Ask("Student Name: "));

                Console.WriteLine("Student Grades: ");
                newStudent.SetGrades(int.Parse(Util.Console.Ask("Student Name: ")));

                students.Add(newStudent);
                Student.count++;
                Console.WriteLine(Student.count);

                Console.WriteLine("Add another? y/n");
                if (Console.ReadLine() != "y")
                {
                    adding = false;
                }
            }
            foreach (var student in students)
            {
                Console.WriteLine("Name: {0}, Grades: {1}", student.GetName(), student.GetGrades());
            }
        }
    }

    class Student
    {
        static public int count = 0;
        private string name;
        private int grades;
        private int Birthday;
        private string Address;
        private string Phone;

        public int Grades
        {
            set { grades = value; }
        }

        public void SetName(string name)
        {
            this.name = name;

        }

        public string GetName()
        {
            return name;
        }

        public void SetGrades(int grades)
        {
            this.grades = grades;

        }
        public int GetGrades()
        {
            return grades;
        }
    }
}
```

## 6. Polymorphism

### Method Overriding

Modifying the implementation of an inherited method 

If a declare a method as virtual in the base class, we can override it in a derived class.

```csharp
public class Shape
{
	public virtual Draw()
	{
		// Default implementation for all derived classes
	}
}

public class Circle : Shape
{
	public override void Draw()
	{
		//change implementation for derived class
	}
}
			
```

## 7. Abstraction

Indicates that a class or a member is missing implementation.

In the above example of Method Overriding, we have saw that the Shape class which is also the base class has a method Draw() which is overrides in the derived class Circle. We have done this because we know that Circle can be drawn but how can we Draw a class called shape, so here we declare shape class abstract and let every class know that it is missing implementation and that implementation must be provided by the derived classes. 

```csharp
public abstract class Shape
{
// draw method is made abstract that's why it dosn't have body
	public abstract Draw();

}

public class Circle : Shape
{
	public override void Draw()
	{
		//change implementation for derived class
	}
}
```

**Points to Remember for Abstraction:**

- Do not include implementation.
- If a member is declared as abstract, the containing class needs to be declared as abstract too

    ```csharp
    public abstract class Shape
    {
    	public abstract void Draw();
    }
    ```

- In a derived class you must implement all abstract members in the base abstract class.
- Cannot be instantiated, means you cannot create an object of an abstract class.

**Why to use Abstract?**

- When you want to provide some common behaviour, while forcing other developers to follow you design.

## 8. Interface

Interface is the more advance form of the Abstraction, it is like a class which defines method, but, unlike the class an interface never implements methods, the method declared in an interface are by default abstract.

- Interfaces specify what a class must do and not how. It is the blueprint of the class.
- An Interface is about capabilities like a Player may be an interface and any class implementing Player must be able to (or must implement) move(). So it specifies a set of methods that the class has to implement.
- If a class implements an interface and does not provide method bodies for all functions specified in the interface, then the class must be declared abstract.

### Why we use Interface?

- It is used to achieve total abstraction.
- It is also used to achieve loose coupling.
- It is used to achieve multiple inheritance which can't be achieved by class. It is used to achieve fully abstraction because it cannot have method body.

## More About Interface:

- An interface is simply a declaration of the capabilities (or services) that a class should provide

    ```csharp
    public interface ITaxCalculator {

    	int Calculate();
    }
    ```

    This interface states a class that wants to play the role of a tax calculator, should provide a method called Calculate() that takes no parameters and returns an int. The implementation of this class might look like this:

    ```csharp
    public class TaxCalculator : ITaxCalculator
    {
    	public void Calculate() {
    		// implementation will come here
    	}
    }
    ```

- So interface is purely a declaration. Members of an interface do not have implementation.
- An interface can only declare methods and properties, but not fields(because fields are about implementation details).
- Members of an interface do not have access modifiers.
- Interface help building loosely coupled applications. We reduce the coupling between two classes by putting an interface between them. This way, if one of these classes changes, it will have no impact on the class that is dependent on that.

### Interface and Testability

- Unit testing is part of the automated practice which helps improve the quality of our code. With automated testing, we write code to test our own code. This helps catching bugs early on as we change the code.
- In order to unit test a class, we need to isolate(means a class should not be dependent on another class) it.
- A class that has tight dependencies to other classes cannot be isolated
- to solve this problem, we use an interface. Here is an e.g.,

    ```csharp
    public class OrderProcessor 
    {
    	 private IShippingCalculator _calculator;
    	 
    	 public Customer(IShippingCalculator calculator)
    	 {
    		 _calculator = calculator;
    	 }
     …
    }
    ```

    So here, OrderProcessor is not Dependent on the ShippingCalculator class. It's only dependent on an interface (IShippingCalculator). If we change the code inside the ShippingCalculator(eg add a new method or change the method implementations) it will have no impact on OrderProcessor(as long as the interface is kept the same).

### Interface and Extensibility

- We can use interfaces to change our application's behaviour by "extending" it code (rather than changing the existing code).
- If a class is dependent on an interface, we can supply a different implementation of that class at runtime. This way, the behaviour of the application changes without any impact on that class.
- For example, let's assume our DbMigrator class is dependent on an ILogger interface. At runtime, we can supply a ConsoleLogger to log the messages on the console. Later, we may decide to log the messages in a file(or a database). We can simply create a new class that implements the ILogger interface and inject it into DBMigrator.

### Interface and Inheritance

- One of the common misconceptions about interfaces is that they are used to implement multiple inheritance in C#. This is fundamentally wrong,
- With inheritance, we write code once and re-use it without the need to type all that code again.
- With interfaces, we simply declare the members the implementing class should contain. Then we need to type all that declaration along with the actual implementation in that class. So, code is not inherited, even the declaration of the members!

# Error and Debugging

## 1. Exception Handling

To catch and an exception in C# we use try/catch block which help us to specify the type of error.

```csharp
using System;
using System.Collections.Generic;

namespace StudentTracker
{
    class Program
    {
        static void Main(string[] args)
        {
            Import();
            var students = new List<Student>();

            var adding = true;

            while (adding)
            {
                try
                {
                    var newStudent = new Student();

                    newStudent.SetName(Util.Console.Ask("Student Name: "));

                    newStudent.Grade = int.Parse(Util.Console.Ask("Student Grade: "));

                    newStudent.SetPhone(Util.Console.Ask("Student's Phone: "));

                    students.Add(newStudent);
                    Student.count++;

                    Console.WriteLine(Student.count);

                    Console.WriteLine("Add another? y/n");
                    if (Console.ReadLine() != "y")
                    {
                        adding = false;
                    }
                    foreach (var student in students)
                    {
                        Console.WriteLine("Name: {0}, Grades: {1}", student.GetName(), student.GetGrades());
                    }
                }

                catch(FormatException)
                {
                    Console.WriteLine("Error, Input was not a number!");
                }

                catch (Exception)
                {

                    Console.WriteLine("Error, adding student please try again!");
                }
            }

            static void Import()
            {
                var importedStudent = new Student("Sanskar Gupta", 20);
                Console.WriteLine(importedStudent.GetName());
            }
        }

        class Member
        {
            protected string name;
            protected string address;
            protected string phone;

            public void SetName(string name)
            {
                this.name = name;

            }

            public string GetName()
            {
                return name;
            }

            public void SetAddress(string address)
            {
                this.address = address;
            }

            public string GetAddress()
            {
                return address;
            }

            public void SetPhone(string phone)
            {
                this.phone = phone;
            }

            public string GetPhone()
            {
                return phone;
            }
        }

        class Student : Member
        {
            static public int count = 0;
            public int grades;
            private int Birthday;

            public Student()
            {

            }
            public Student(string name, int grades)
            {
                this.name = name;
                this.grades = grades;
            }

            public int Grade
            {
                set { grades = value; }
            }

            public int GetGrades()
            {
                return grades;
            }
        }

        class Teacher : Member
        {
            public string Subject;
        }
    }
}
```

## 2. Throwing Exceptions

In our custom Console.cs package we have created a input-output system for string and now we have added the integer method also so to catch the error directly from the Console.cs package we will implement try/catch block there as well,

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace Util

{
    class Console
    {
        static public string Ask(string question)
        {
            System.Console.WriteLine(question);
            return System.Console.ReadLine();
        }

        static public int AskInt(string question)
        {
            try
            {
                System.Console.WriteLine(question);
                return int.Parse(System.Console.ReadLine());
            }
            catch (Exception)
            {
                throw new FormatException("Error, Input number was not a number");
            }
            
        }
    }
}
```

```csharp
using System;
using System.Collections.Generic;

namespace StudentTracker
{
    class Program
    {
        static void Main(string[] args)
        {
            Import();
            var students = new List<Student>();

            var adding = true;

            while (adding)
            {
                **try
                {
                    var newStudent = new Student();

                    newStudent.SetName(Util.Console.Ask("Student Name: "));

                    newStudent.Grade = Util.Console.AskInt("Student Grade: ");

                    newStudent.SetPhone(Util.Console.Ask("Student's Phone: "));

                    students.Add(newStudent);
                    Student.count++;

                    Console.WriteLine(Student.count);

                    Console.WriteLine("Add another? y/n");
                    if (Console.ReadLine() != "y")
                    {
                        adding = false;
                    }
                    foreach (var student in students)
                    {
                        Console.WriteLine("Name: {0}, Grades: {1}", student.GetName(), student.GetGrades());
                    }
                }**

                **catch(FormatException msg)
                {
                    Console.WriteLine(msg.Message);
                }

                catch (Exception)
                {

                    Console.WriteLine("Error, adding student please try again!");
                }**
            }

            static void Import()
            {
                var importedStudent = new Student("Sanskar Gupta", 20);
                Console.WriteLine(importedStudent.GetName());
            }
        }

        class Member
        {
            protected string name;
            protected string address;
            protected string phone;

            public void SetName(string name)
            {
                this.name = name;

            }

            public string GetName()
            {
                return name;
            }

            public void SetAddress(string address)
            {
                this.address = address;
            }

            public string GetAddress()
            {
                return address;
            }

            public void SetPhone(string phone)
            {
                this.phone = phone;
            }

            public string GetPhone()
            {
                return phone;
            }
        }

        class Student : Member
        {
            static public int count = 0;
            public int grades;
            private int Birthday;

            public Student()
            {

            }
            public Student(string name, int grades)
            {
                this.name = name;
                this.grades = grades;
            }

            public int Grade
            {
                set { grades = value; }
            }

            public int GetGrades()
            {
                return grades;
            }
        }

        class Teacher : Member
        {
            public string Subject;
        }
    }
}
```

# Enumerators

Enumerators or enum is user defined data types. It is mainly used to assign names to integral constants, the names make a program easy to read and maintain.

```csharp
using System;
using System.Collections.Generic;

namespace SchoolTracker
{

    enum School
    {
        Bishop_WestCott_School,
        St_Merry_School,
        Delhi_Public_School
    }
    class Program
    {

        static List<Student> students = new List<Student>();

        static void Main(string[] args)
        {

            var adding = true;

            while (adding)
            {
                var newStudent = new Student();

                newStudent.Name = Util.Console.Ask("Student Name: ");

                var result = int.TryParse(Util.Console.Ask("Student Grade: "), out newStudent.Grade);

                if (!result)
                {
                    Console.WriteLine("error, please enter a number");
                }

                newStudent.Birthday = Util.Console.Ask("Student Birthday: ");

                newStudent.Address = Util.Console.Ask("Student Address: ");

                newStudent.Phone = Util.Console.Ask("Student Phone Number: ");

                newStudent.school = (School)Util.Console.AskInt("Enter the School Name: 0: Bishop Westcott School \n 1: St. Merry School 2: \n Delhi Public School \n");

                students.Add(newStudent);
                Student.Count++;
                Console.WriteLine("Student Count: {0}", Student.Count);

                Console.WriteLine("Add another? y/n");

                if (Console.ReadLine() != "y")
                    adding = false;
            }

            foreach (var student in students)
            {
                Console.WriteLine("Name: {0}, Grade: {1}", student.Name, student.Grade);
            }

            Export();
        }

        static void Import()
        {
            var importedStudent = new Student("Jenny", 86, "birthday", "address", "9883887432");
            Console.WriteLine(importedStudent.Name);
        }

        static void Export()
        {
            foreach (var student in students)
            {
                switch (student.school)
                {
                    case School.Bishop_WestCott_School:
                        Console.WriteLine("Exporting to Bishop Westcott School");
                        break;

                    case School.St_Merry_School:
                        Console.WriteLine("Exporting to St. Merry School");
                        break;

                    case School.Delhi_Public_School:
                        Console.WriteLine("Exporting to Delhi Public School");
                        break;
                }
            }
        }
    }

    class Member
    {
        public string Name;
        public string Address;
        protected string phone;

        public string Phone
        {
            set { phone = value; }
        }
    }

    class Student : Member
    {
        static public int Count = 0;

        public int Grade;
        public string Birthday;
        public School school;

        public Student()
        {

        }

        public Student(string name, int grade, string birthday, string address, string phone)
        {
            Name = name;
            Grade = grade;
            Birthday = birthday;
            Address = address;
            Phone = phone;
        }

        public void SetSchool(School school)
        {
            this.school = school;
        }

        public School GetSchool()
        {
            return school;
        }
    }

    class Teacher : Member
    {
        public string Subject;
    }
}
```

if you want to convert enum to string you can do this,

```csharp
public enum ShippingMethods {
	RegularShipping = 1,
	RegisteredAirMail = 2,
	Express = 3
}

class Program {
	
	var method = ShippingMethod.Express
	Console.WriteLine(method.ToString());
	
}
```

if you want to convert string to an enum, then you can do this,

```csharp
public enum ShippingMethods {
	RegularShipping = 1,
	RegisteredAirMail = 2,
	Express = 3
}

class Program {
	
	
	var methodName = "SuperExpress";
	var shippingMethod = (ShippingMethod) Enum.Parse(typeof(ShippingMethod), methodName));
	
}
```

# Extension Methods

We can an extension in C# which can convert string to integer, for that we create a ExtensionMethods Class in our Console.cs file,

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace Util

{
    static public class ExtensionMethods
    {
        public static int toInt(this string value)
        {
            return int.Parse(value);
        }
    }

    class Console
    {
        static public string Ask(string question)
        {
            System.Console.WriteLine(question);
            return System.Console.ReadLine();
        }

        static public int AskInt(string question)
        {
            try
            {
                System.Console.WriteLine(question);
                return System.Console.ReadLine().toInt();
            }
            catch (Exception)
            {
                throw new FormatException("Error, Input number was not a number");
            }
            
        }
    }
}
```
