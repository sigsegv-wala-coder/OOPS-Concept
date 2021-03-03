# OOPS-Concept
------------------------------------------------------------------------------------------
To build a class, the basic layout is as follows :

class student{                   // Here we are creating a student class which consists of few properties of students.
  int rollNumber;
  int age;
};
---------------------------------------------------------------------------------------------
To statically and dynamically create objects examples : 

Let us create a object S1 of student class as mentioned above. Statically

student S1;
student S2;

S1 and S2 will contain properties listed in student class.
Now dynamically,

student *S3 = new student;           // compare with dynamic declaration of variable. student in place of int data type
student *S4 = new student;           // e.g. int *p = new int ... similarly student *S = new student;

------------------------------------------------------------------------------------------------

Assign values for the objects properties. 
Statically : 
S1.rollNumber = 50;
S2.age = 20;
Dynamically : 

(*S3).age = 15;
(*S4).rollNumber = 100;

S3 -> age = 15;             // Remember the arrow sign. We can use both the notations
S4 -> rollNumber = 100;

--------------------------------------------------------------------------------------------------

Access Modifiers : Public       Private         Protected

Public properties can be accessed and changed in the main function 
Private properties can only be accessed in the class parenthesis. We can't change them directly in the main function unlike public properties

But with the help of additional function which is called getters and setters we can access the private functions in the main one.

Here is the example to make things clear - 

#include <iostream>
using namespace std;

class student{
  public : 
  
     int rolNumber;
  
  private : 
  
     int age;
  
  public : 
  
    void display(){
  
    cout<< age << " " << rollNumber << endl ;
  }
    
    int getAge(){
      return age;
    }
    
    void setAge(int a , int password){           //If we can change the private functions by the help of these additional functions
      if(password!=123){                         // Then what's the use. We can actually put constraints for updating the value
        return;                                  // Like if the password is correct then only you can access it. 
      }
      if(a<0){
        return;
      }
      
      age = a;
    }
};

int main(){
  student S1;
  student *S2 = new student;

  S1.setAge(25 , 123);
  S2 -> setAge(20, 222);

  cout << "S1 age : " << S1.getAge() <<endl;
  cout<< "S2 age : " << S2 -> getAge() <<endl; 

  S1.display();
  S2 -> display();
  
}
------------------------------------------------------------------------------------------------------------------------- 
Constructors : 

A constructor is called everytime we create an object. For example, like in student class, if we create a student S1, 
then a default constructor is called whose syntax is given below. Also, we can make our constructor so that instead of
the default one, the one which we made is called. Also, for an object, a constructor is called only once in a lifetime.

what happens is when we create a student S1, then S1.student() is called internally.

// Default constructor
student() {
  cout<< "Constructor called" << endl;   // Now if we create a student S1 , then "Constructor called" will be printed first.
}
If we want to initialize the object properties with our values, then we have to pass our values to constructor as follows : 

// Parametrized constructors
student( int r ) {
  rollNumber = r;
}

student ( int r , int a) {
    r = rollNumber;
    a = age;
}

this keyword

Suppose while passing the arguments to constructors, we want same variable name as our properties like : 

student ( int rollNumber , int age) {
    age = age;
    rollNumber = rollNumber;
}

There is a confusion regarding the scope of the variable. That's why we have special keyword known as this keyword.
What 'this' keyword does is , it stores the address of the current object.

student ( int rollNumber , int age) {
    this -> age = age;
    this -> rollNumber = rollNumber;
}

// Copy Constructor
The function of copy constructor is to copy the properties of an object to other while creation.
We can't use the copy constructor after creation of the object.

student S2(S1); //copy the properties of S1 to S2.

// Copy Assignment operator (=)

If we want to copy the properties after the creation, then this operator is used.

student S1( 10 , 18);

student S2 (20 , 16);

S2 = S1;

// Destructors

It is used to deallocate the memory of object. Like constructors, it is also called only once in an object's lifetime.
It's syntax is like

~ student(){
  
}
Note - if we create an object dynamically like 
student *S3 = new student;

then to deallocate the memory, we have to call "delete S3" explicitly, then the destructor will function.
-----------------------------------------------------------------------------------------------------------------------------------------







