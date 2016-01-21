# Programming-Language-Apex-Notes

Apex is a proprietary language which has been developed by Salesforce.com. Apex is a strongly typed, object-oriented programming language that allows developers to execute flow and transaction control statements on the Force.com platform server in conjunction with calls to the Force.com API.

#What is Apex?

It has a Java-like syntax and acts like database stored procedures. It enables the developers to add business logic to most system events, including button clicks, related record updates, and Visualforce pages.Apex code can be initiated by Web service requests and from triggers on objects. Apex is included in Performance Edition, Unlimited Edition, Enterprise Edition, and Developer Edition

![apex code execution scenario](http://www.tutorialspoint.com/apex/images/apex_code_execution_scenario.jpg)

#Features of Apex as a Language

##Integrated

Apex has built in support for DML operations like INSERT, UPDATE, DELETE and also DML Exception handling. It has support for inline SOQL and SOSL query handling which returns the set of sObject records. We will study the sObject, SOQL, SOSL in detail in future chapters.

##Java like syntax and easy to use

Apex is easy to use as it uses the syntax like Java. For example, variable declaration, loop syntax and conditional statements.

##Strongly Integrated With Data

Apex is data focused and designed to execute multiple queries and DML statements together. It issues multiple transaction statements on Database.

##Strongly Typed

Apex is strongly typed language. It uses direct reference to schema objects like sObject and any invalid reference quickly fails if it is deleted or if is of wrong data type.

##Multitenant Environment

Apex runs in a multitenant environment. Consequently, the Apex runtime engine is designed to guard closely against runaway code, preventing it from monopolizing shared resources. Any code that violates limits fails with easy-to-understand error messages.

##Upgrades Automatically

Apex is upgraded as part of Salesforce releases. We don't have to upgrade it manually.

##Easy Testing

Apex provides built-in support for unit test creation and execution, including test results that indicate how much code is covered, and which parts of your code could be more efficient.

#When Should Developer choose Apex?

Apex should be used when we are not able to implement the complex business functionality using the pre-built and existing out of the box functionalities. Below are the cases where we need to use apex over Salesforce configuration.

#Apex Applications

We can use Apex when we want to:

1.Create Web services with integrating other systems.
2.Create email services for email blast or email setup.
3.Perform complex validation over multiple objects at the same time and also custom validation implementation.
4.Create complex business processes that are not supported by existing workflow functionality or flows.
5.Create custom transactional logic (logic that occurs over the entire transaction, not just with a single record or object) like using the Database methods for updating the records.
Perform some logic when a record is modified or modify the related object's record when there is some event which has caused the trigger to fire.


#Working Structures of Apex

![workflow of apex](http://www.tutorialspoint.com/apex/images/apex_compilation_of_apex_code.jpg)

#Apex don't Support

1.It cannot show the elements in User interface.
2.You cannot change the standard SFDC provided functionality and also it is not possible to prevent the standard functionality execution.
3.Temporary file creation is not supported.
4.Creating multiple threads is also not possible as we could do it in other languages.

````

String myString = 'MyString';
System.debug('Value of String Variable ' + myString);


// Declaring Enum For Chemical Compounds
public enum Compounds {HCL, H2S04, NACL, HG}
Compounds objC =  Compounds.HCL;
System.Debug('objC value:  ' + objC);


// Apex Variables

String productName = 'HCL';
Integer i=0;
Set<string> setOfProducts = new Set<string>();
Map<id, string> mapOfProductIdToName = new Map<id, string>();

// Declaring Variables

String strName = 'My String';//String variable declaration
Integer myInteger = 1;//Integer variable declaration
Boolean mtBoolean = true;//Boolean variable declaration

// Apex Variables are case sensitive

Integer m = 100;
for (Integer i = 0; i<10; i++) {
    integer m=1; //This statement will throw an error as m is being declared again
    System.debug('This code will throw error');
}


//Declare variable Products
List<string> Products = new List<strings>();
Products.add('HCL');

//You cannot declare this variable in this code clock or sub code block again
//If you do so then it will throw the error as the previous variable in scope
//Below statement will throw error if declared in same code block
List<string> Products = new List<strings>();

//Defining array

String [] arrayOfProducts = new List<String>();

//Adding elements in Array

arrayOfProducts.add('HCL');
arrayOfProducts.add('H2SO4');
arrayOfProducts.add('NACL');
arrayOfProducts.add('H2O');
arrayOfProducts.add('N2');
arrayOfProducts.add('U296');

for (Integer i = 0; i<arrayOfProducts.size(); i++) {
    //This loop will print all the elements in array
    system.debug('Values In Array: '+arrayOfProducts[i]);   
}

// Apex Constants

public class CustomerOperationClass {
    static final Double regularCustomerDiscount = 0.1;
    static Double finalPrice = 0;
    public static Double provideDiscount (Integer price) {
        //calculate the discount
        finalPrice = price - price*regularCustomerDiscount;
        return finalPrice;
    }
}

//To see Output of above class, you have to execute the following code in developer console anonymous window:

Double finalPrice = CustomerOperationClass.provideDiscount(100);
System.debug('finalPrice '+finalPrice);

````

# Methods For Lists

1. size();
2. add();
3. get();
4. clear();
5. set();

````
//Initialize the List
List<string> ListOfStatesMethod = new List<string>();

//This statement would give null as output in Debug logs
System.debug('Value of List'+ ListOfStatesMethod);

//Add element to the list using add method
ListOfStatesMethod.add('New York');
ListOfStatesMethod.add('Ohio');

//This statement would give New York and Ohio as output in Debug logs
System.debug('Value of List with new States'+ ListOfStatesMethod);

//Get the element at the index 0
String StateAtFirstPosition = ListOfStatesMethod.get(0);

//This statement would give New York as output in Debug log
System.debug('Value of List at First Position'+ StateAtFirstPosition);

//set the element at 1 position
ListOfStatesMethod.set(0, 'LA');

//This statement would give output in Debug log
System.debug('Value of List with element set at First Position'+ ListOfStatesMethod[0]);

//Remove all the elements in List
ListOfStatesMethod.clear();

//This statement would give output in Debug log
System.debug('Value of List'+ ListOfStatesMethod);

````

# Class Variables

````
[public | private | protected | global] [final] [static] data_type variable_name [=value]

````

# Class Methods

````
  [public | private | protected | global]
  [override]
  [static]
  return_data_type method_name(input parameters)
  {
    // Method Body Goes Here
  }  
````

#sObject Creation

````
// Execute the below code in Developer Console by simply pasting it 

// Standard Object initialization on for Account sObject


Account objAccount = 'Testr Account'; // Assigning the value to field name of Account
objAccount.Name = 'Testr account';
objAccount.Description = 'Testr Account';

insert objAccount; // creating the record using DML
System.debug("Records has been created " + objAccount);

// custom sObject initialization and assignment of values to field

APEX_Customer_c objCustomer = new APEX_Customer_c();
objCustomer.Name = 'ABC Customer';
objCustomer.APEX_Customer_Description_c = 'Test Description';
insert objCustomer;
System.debug('Records has been created' + objCustomer);

````

