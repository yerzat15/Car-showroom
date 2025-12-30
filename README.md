Assignment 2: Vehicle Management System
Project Overview
This project implements a Vehicle Management System that demonstrates core Object-Oriented Programming (OOP) principles including inheritance, abstraction, composition, and aggregation. The system manages different types of vehicles (Cars, Motorcycles, and Trucks) and their associated drivers.
Key Features:

    Abstract Vehicle superclass defining common behavior
    Three concrete vehicle subclasses: Car, Motorcycle, and Truck
    Driver class demonstrating composition and aggregation relationships
    Polymorphic array processing of different vehicle types
    Method overriding for customized behavior per vehicle type

OOP Concepts Demonstrated:

1. Inheritance: All vehicle types inherit from the abstract Vehicle class
2. Abstraction: Vehicle defines abstract methods that subclasses must implement
3. Encapsulation: Private fields with controlled access through methods
4. Polymorphism: Array of Vehicle references holding different vehicle types
5. Composition: Each Vehicle has-a Driver (strong relationship)
6. Aggregation: One Driver can be associated with multiple Vehicle objects (weak relationship)


Class Hierarchy
1. Vehicle (Abstract Superclass)
Purpose: Serves as the blueprint for all vehicle types. Contains common attributes and defines abstract methods that must be implemented by subclasses.
Fields:

    protected String brand - Vehicle manufacturer (accessible to subclasses)
    protected int year - Year of manufacture (accessible to subclasses)
    private Driver driver - Associated driver (composition)

Abstract Methods (must be overridden):

    void startEngine() - Each vehicle type implements its own start behavior
    void stopEngine() - Each vehicle type implements its own stop behavior

Concrete Methods:

    void displayInfo() - Shows brand and year (inherited by all subclasses)
    void setDriver(Driver driver) - Assigns a driver to the vehicle
    Driver getDriver() - Returns the assigned driver
    void displayDriverInfo() - Shows information about the assigned driver

Access Modifiers Used:

    protected: Allows subclasses to access brand and year directly
    private: Keeps driver field encapsulated within the Vehicle class


2. Car (Subclass of Vehicle)
Additional Fields:

    private int doors - Number of doors
    private String fuelType - Type of fuel (Gasoline, Diesel, Electric, Hybrid)

Constructor:
    public Car(String brand, int year, int doors, String fuelType)

Uses super(brand, year) to call parent constructor (constructor chaining)

Overridden Methods:

    startEngine(): Displays "Turn key and press start button"
    stopEngine(): Displays "Engine shut down smoothly"
    displayInfo(): Calls super.displayInfo() then adds car-specific details


3. Motorcycle (Subclass of Vehicle)
Additional Field:

    private boolean hasSidecar - Whether the motorcycle has a sidecar

Constructor:
    public Motorcycle(String brand, int year, boolean hasSidecar)

Uses super(brand, year) to call parent constructor

Overridden Methods:

    startEngine(): Displays "Kick start and throttle"
    stopEngine(): Displays "Kill switch activated"
    displayInfo(): Calls super.displayInfo() then shows sidecar status


4. Truck (Subclass of Vehicle)
Additional Fields:

private double capacity - Load capacity in tons
private int numAxles - Number of axles

Constructor:
    public Truck(String brand, int year, double capacity, int numAxles)

Uses super(brand, year) to call parent constructor

Overridden Methods:

    startEngine(): Displays "Diesel engine rumbling"
    stopEngine(): Displays "Heavy engine powered down"
    displayInfo(): Calls super.displayInfo() then shows capacity and axles


5. Driver Class
Purpose: Represents a person who can drive vehicles. Demonstrates composition (Vehicle has-a Driver) and aggregation (Driver can have multiple Vehicles).
Fields:

    private String name - Driver's full name
    private String licenseNumber - Driver's license number

Methods:

    void displayDriverInfo() - Displays name and license number
    Getters and setters for all fields

Relationship Types:

    Composition with Vehicle: Each vehicle object contains a Driver reference
    Aggregation: A single Driver object can be referenced by multiple Vehicle objects


Instructions to Compile and Run
Prerequisites

    Java Development Kit (JDK) 8 or higher
    Command line terminal or IDE (Eclipse, IntelliJ IDEA, VS Code)

Compilation
Navigate to the src/ directory and compile all Java files:
    cd src
    javac *.java
Or compile individually:
    javac Vehicle.java
    javac Car.java
    javac Motorcycle.java
    javac Truck.java
    javac Driver.java
    javac Main.java
Execution
Run the main program:
    java Main

Expected Output
The program will:

1. Create multiple vehicles (2 cars, 2 motorcycles, 1 truck)
2. Create three drivers
3. Assign drivers to vehicles (demonstrating aggregation)
4. Process all vehicles in a loop, calling:
    startEngine()
    displayInfo()
    displayDriverInfo()
    stopEngine()
6. Display driver-vehicle associations
7. Show fleet statistics


Program Output Screenshots
Sample Output:
![img_1.png](img_1.png)![img_3.png](img_3.png)![img_4.png](img_4.png)
Reflection
What I Learned
This assignment helped me understand inheritance and abstraction in Java. I learned that an abstract class is like a template that forces all subclasses to implement certain methods. For example, every vehicle must have startEngine() and stopEngine() methods, but each type (Car, Motorcycle, Truck) can implement them differently.
Using the super keyword was new to me. When I write super(brand, year) in a Car constructor, it calls the Vehicle constructor first. This makes sense because you need to set up the basic vehicle information before adding car-specific details like doors and fuel type.
I also learned the difference between composition and aggregation. Composition means one object owns another - like a Vehicle owns its Driver. Aggregation is looser - one Driver can work with many Vehicles. This is just like real life where one person can drive different cars.
Challenges Faced
At first, I didn't understand when to use protected or private. I made everything private, but then my Car class couldn't access the brand field from Vehicle. I learned that protected lets subclasses see parent fields while still hiding them from other classes.
Polymorphism was confusing at first. I created an array of type Vehicle[] but put Cars, Motorcycles, and Trucks in it. I was surprised that when I called startEngine(), each vehicle type ran its own version of the method, not the parent's version. The @Override annotation helped me make sure I was overriding methods correctly.
Benefits of OOP Principles
Encapsulation keeps data safe. By making fields private and using getters/setters, I control how data is accessed and changed. This prevents mistakes like setting a negative year or null brand name.
Inheritance saved me a lot of code. Instead of writing driver management code three times (once for Car, Motorcycle, and Truck), I wrote it once in Vehicle and all subclasses got it automatically.
Polymorphism made my main program much simpler. I could loop through one array of vehicles instead of having separate loops for cars, motorcycles, and trucks. The program automatically called the right method for each vehicle type.
This assignment showed me that OOP is not just theory - it actually makes code easier to write, understand, and change later.

Repository Structure
assignment2-vehicle-system/
|-- src/
│   |-- Vehicle.java          
│   |-- Car.java            
│   |-- Motorcycle.java    
│   |-- Truck.java        
│   |-- Driver.java      
│   |-- Main.java           
|-- docs/
│   |-- screenshots/        
│   |-- uml-diagram.png    
|-- README.md            
|-- .gitignore