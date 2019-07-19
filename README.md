# Structs and Classes Lab - 2


## Question 1
​
​Using the Room struct below, write code that demonstrates that it is a value type.
​
​```swift
​struct Room {
​let maxOccupancy: Int
​let length: Double
​let width: Double
​}
​```
​```swift
​var firstRoom = Room(maxOccupancy: 1, length: 1.1, width: 12.1)
​var secondRoom = firstRoom
​secondRoom = Room(maxOccupancy: 2, length: 3.2, width: 4.3)
​
​print(firstRoom)
​print(secondRoom)
​```
​## Question 2
​
​Using the Bike class below, write code that demonstrates that it is a reference type.
​
​```swift
​class Bike {
​var wheelNumber = 2
​var hasBell = false
​}
​```
​```swift
​var myBike = Bike()
​var yourBike = myBike
​yourBike.wheelNumber = 3
​print(myBike.wheelNumber)
​print(yourBike.wheelNumber)
​```
​## Question 3
​
​a. Given the Animal class below, create a Bird subclass with a new `canFly` property.
​
​```swift
​class Animal {
​var name: String = ""
​func printDescription() {
​print("I am an animal named \(name)")
​}
​}
​```
​
​```swift
​class Bird: Animal {
​var canFly: String
​}
​```
​
​b. Override the printDescription method to have the instance of the Bird object print out its name and whether it can fly
​
​```swift
​class Bird: Animal {
​var canFly: String
​
​init(canFly: String) {
​self.canFly = canFly
​}
​override func printDescription() {
​name = "sparrow"
​print("I am an animal named \(name) and I \(canFly) fly.")
​}
​}
​
​var sparrow = Bird(canFly: "can")
​sparrow.printDescription()
​```
​
​
​## Question 4
​
​```swift
​class Bike {
​let wheelNumber = 2
​let wheelWidth = 1.3
​var hasBell = true
​func ringBell() {
​if hasBell {
​print("Ring!")
​}
​}
​}
​```
​
​
​a. Create a `LoudBike` subclass of Bike.  When you call `ringBell` it should ring the bell in all caps.
​
​```swift
​class LoudBike: Bike {
​override func ringBell() {
​if hasBell {
​print("RING!!!!!!!!!!!!!!!!!!!!")
​}
​}
​}
​
​```
​b. Give `LoudBike` a new method called `ringBell(times:)` that rings the bell a given number of times
​
​```swift
​class LoudBike: Bike {
​override func ringBell() {
​if hasBell {
​print("RING!!!!!!!!!!!!!!!!!!!!")
​}
​}
​func ringBellTheOtherOne(times: Int) {
​if hasBell{
​for _ in 1...times {
​print("RING!!!!!!!!!!!!!!!!!!!!")
​}
​}
​}
​}
​
​var newBike = LoudBike()
​newBike.ringBellTheOtherOne(times: 4)
​```
​
​## Question 5
​
​```swift
​class Shape {
​var name: String { return "This is a generic shape" }
​var area: Double { fatalError("Subclasses must override the area") }
​var perimeter: Double { fatalError("Subclasses must override the perimeter") }
​}
​```
​
​a. Given the `Shape` object above, create a subclass `Square` with a property `sideLength` with a default value of 5.
​
​```swift
​class Square: Shape {
​var sideLength = 5
​}
​```
​
​b. Override the `area` and `perimeter` computed values so the return the area/perimeter of the square as appropriate
​
​```swift 
​class Square: Shape {
​var sideLength = 5.0
​override var area: Double {
​get {
​return sideLength * sideLength
​}
​}
​override var perimeter: Double {
​get {
​return sideLength * 4
​}
​}
​}
​
​var square2 = Square()
​square2.area
​square2.perimeter
​```
​
​c. Override the `name` property of `Square` so that it returns a String containing its name ("Square") and its area and perimeter
​
​```swift
​class Square: Shape {
​var sideLength = 5.0
​override var area: Double {
​get {
​return sideLength * sideLength
​}
​}
​override var perimeter: Double {
​get {
​return sideLength * 4
​}
​}
​override var name: String {
​get {
​
​return "My name is Square, my area is \(area) and my perimeter is \(perimeter)"
​}
​}
​}
​
​var square2 = Square()
​square2.area
​square2.perimeter
​square2.name
​```
​
​d. Create a class `Rectangle` that subclasses from `Shape`.  Give it a `width` property with a default value of 6 and a `height` property with a default value of 4
​
​```swift 
​class Rectangle: Shape {
​var width = 6
​var height = 4
​}
​```
​
​e. Override the `name` property of `Rectangle` so that it returns a String containing its name ("Rectangle") and its area and perimeter.
​
​```swift
​class Rectangle: Shape {
​var width = 6.0
​var height = 4.0
​
​override var area: Double {
​get {
​return width * height
​}
​}
​override var perimeter: Double {
​get {
​return (width * 2) + (height * 2)
​}
​}
​override var name: String {
​get {
​return "My name is \(type(of: self)), my area is \(area) and my perimeter is \(perimeter)"
​}
​}
​}
​
​var rectange = Rectangle()
​rectange.name
​
​```
​
​f. (BONUS) What happens when you run the code below?  Explain why.
​
​```swift
​var myShapes = [Shape]()
​
​myShapes.append(Square())
​myShapes.append(Rectangle())
​
​for shape in myShapes {
​print("This is a \(shape.name) with an area of \(shape.area) and a perimeter of \(shape.perimeter)")
​}
​```
​The code creates an empty Shape.Type array, appends both the subclasses square and rectangle to the array, and then creates a for-loop that iterates through the array and prints out a string with the shape name, area and perimeter at each index of myShapes.
​
​## Question 6
​
​a. Given the Point object below, complete the `distance` method so that it returns the distance between a given point.
​
​The equation for the distance formula can be found [here](https://www.mathsisfun.com/algebra/distance-2-points.html) and is give by:
​
​```swift
​let horizontalDistance = pointOneXValue - pointTwoXValue
​let verticalDistance = pointOneYValue - pointTwoYValue
​let distanceBetweenTwoPoints = sqrt(horizontalDistance * horizontalDistance + verticalDistance * verticalDistance)
​```
​
​`sqrt` is a method in Swift that gives the square root.  Make sure to have `import Foundation` or `import UIKit` to use this method.
​
​```swift
​struct Point {
​let x: Double
​let y: Double
​func distance(to point: Point) -> Double {
​let horizontalDistance = point.x - self.x
​let verticalDistance = point.y - self.y
​let distance = sqrt(horizontalDistance * horizontalDistance + verticalDistance * verticalDistance)
​return distance
​}
​}
​
​let pointOne = Point(x: 0, y: 0)
​let pointTwo = Point(x: 10, y: 10)
​
​print(pointOne.distance(to: pointTwo)) //Prints 14.142135623730951
​```
​
​
​b. Given the above Point object, and Circle object below, add a `contains` method that returns whether or not a given point is on the circle
​
​```swift
​struct Circle {
​let radius: Double
​let center: Point
​}
​
​let pointOne = Point(x: 0, y: 0)
​let circleOne = Circle(radius: 5, center: pointOne)
​let pointTwo = Point(x: 5, y: 0)
​let pointThree = Point(x: 4, y: 0)
​let pointFour = Point(x: sqrt(12.5), y: sqrt(12.5))
​circleOne.contains(pointTwo) //true
​circleOne.contains(pointThree) // false
​circleOne.contains(pointFour) //true
​```
​
​
​
​
​
​
​
​

​
