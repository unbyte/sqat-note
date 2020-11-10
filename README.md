🚧 TBD



# PPT-Driven Notes of SQAT



## 1. Introduction to Software QA and Testing

**The Purpose for Testing** is not to prove anything specific, but to **reduce the risk of using the software**

If our goal is to demonstrate that a program has no errors, then we will be steered subconsciously toward this goal; that is, we tend to select test data that have a low probability of causing the program to fail. On the other hand, if our goal is to demonstrate that a program has errors, our test data will have a higher probability of finding errors. The latter approach will add more value to the program than the former.



### Basic Terminology

- Errors (or mistakes) – A problem that is introduced into a system during development. 
- Faults (defects) - A result of an error. 
  - If a designer makes an error that adds something that we don’t want, the fault is incorrect execution. 
  - If a designer makes an error that misses out something, then the fault is something that is not in the software. 
- Failures – The result when a fault executes. 
- Incidents – The symptoms that indicates that there is a fault. 



#### Relationship

System(Errors → Faults → Failures) → User(Incidents)




### TESTING is a vital part of development

- Make sure people build things with right tools and methods
- Make sure the system has a sensible architecture 
- Use walkthroughs to make sure we agree on what is being done and how it is being done 

**TESTING should balance time, money and quality**



### Joel's Example

- Testing checks your daily building
- Testing shows that bugs have been fixed 
- Testing indicates how you are doing against the schedule
- Testing validates development against the specification
- Usability testing checks you are building what users want



### Software Quality Management

Software Quality Management is concerned with ensuring that developed software systems are ‘fit for purpose.’ 

- We need processes and standards that should help a team to develop high-quality products 
- We need to check that the processes and standards have been followed 
- We will be thinking further about Software Quality and how it can be managed



## 2. Black-Box Testing

### Advantage

You don’t need to know how it is implemented, so

- You can plan tests earlier 
- You can write tests earlier 
- You do not need to be the person who implements the code 
- When the implementation changes, the tests should still work 



### Techniques to identify good test values

- Equivalence Partition(Domain)

  - Identify the equivalence classes. 

  - Design a new test case, with a unique ID, that covers a valid equivalence class which has not yet been 

    tested.

    - Repeat this step until all valid equivalence classes are included 

  - Design a new test case, with a unique ID, that covers an invalid equivalence class which has not yet been tested.

    - Repeat this step until all invalid equivalence classes are included 

- Boundary Value Analysis

  - Boundary Value Analysis works well when the variables are independent and represent bounded physical quantities 
    - E.g. good for temperatures, air speed, etc.

- Decision Tables

- Cause-Effect Graphing

- Error guessing



### How complete is the selection of test cases?

**Weak** vs **Strong**

- **Weak** – Assuming a single fault – choose one value and select test cases for each equivalence partition

-  **Strong** – Assuming multiple faults - choose test cases for the combination of equivalence partitions



**Normal** vs **Robust**

- **Normal** – select values from the ‘valid’ ranges 

- **Robust** – select values from the ‘invalid’ ranges



## 3. White-Box Testing

White-box is based on the implementation.

Black-box testing works well to generate for high-level test cases that check the general logic of the application, while for high confidence, e.g. in safety critical software, need to look at the code and make sure every possibility is covered 

*Still worth doing black-box testing then look at EXTRA tests based on white-box approaches*



### Testing Types

- Static Analysis 

  - Discussed during the Software Lifecycle course 

  - Code Inspection

    - Engineers arrange meetings to review sections of code

    - Ask questions about how the code works with specific (test) cases 

  - The analysis cannot be automated

    - Difficult to repeat the same analysis each time 

  - BUT, code inspections are an effective way to detect potential problems 

- Dynamic Testing with path coverage of code
  - Analyse the different ways that the code can be executed 
  - Write tests so that every path through the program is tested 
    - Remember earlier, statements, decisions, conditions
  - The tests can be automated and repeated 
  - Tool support to check coverage 
  - BUT, we need to update tests when the code changes



Basic principles of path coverage: 

- All independent paths in a module must be traversed at least once
- All conditions (e.g. if statements) are tested for the true and false outcomes 

- Review whether the tests cover the internal data structures used

- Test that loops work for their operational range (difficult to try ALL possible values for loops for the same reason that you cannot try ALL values for parameters). 



### Control Flow Graphing & Basis Paths

- Control Flow Graphs can be used to understand the connections within the code
  - How one part of the code moves to the next part
  - Helps us to understand the control structure
  - Cyclomatic Complexity to measure function complexity 
    - Help for testing 
- Basis Path is an independent path through 
  - Each path represents a path to test



### Control Flow Graph contains 

- Nodes – represents actions in the code. We are particularly interested in conditions that change the flow in the code.

- Edges – Arrows that link the Nodes. 

- Start and Entry Point



### Cyclomatic Complexity

- Calculation that gives an indication of complexity 

- Higher the number, the more complex the code is
- Two similar ways to calculate
  - **Number of Edges – Number of Nodes + 2**
  - Number of condition clauses + 1

- Can use the calculation for testing to indicate a minimum number of tests for a section of code



## 4. Unit Testing

### Definition

Unit-testing is a way to **ensure** that the code you write **adheres to design specifications** and that it **keeps adhering to those specifications as you modify it**

Unit-testing helps you write **robust** and **secure** apps. The essential component of unit-testing is a test case, which tests your code at the lowest testable level, or unit.



### System Under Test (SUT)

- Test one unit at a time in isolation

- Check that all units pass all tests

- Focus on the interface definition of the unit



### Purpose

- Validate whether code is consistent with the design and requirements.
- Discover the errors between requirements, the design and implementation.
  - Errors of **omission** (what was required, but not implemented) 
  - Errors of **commission** (an incorrect implementation)



### Aims

- **Aim:** ensure that module was implemented correctly

- **Input:** detailed specification*

- **Process:** design and implement tests and analyseresults

- **Personnel:** Developers and Testers 

- **Test approaches:** you can use black-box and white-box methods* 

- **Evaluation:** determine if the tests reveal errors. 



### Process

![image-20201110230612209](assets/image-20201110230612209.png)



### Benefits

- The goal of unit testing is to isolate each part of the program and show that the individual parts are correct. 
  - Help to improve confidence in the software’s quality 

- A unit test provides a strict, written contract that the piece of code must satisfy. 
  - Track when the code isn’t satisfying the requirements / design
- Easier to find issues when a test fails
- Unit tests find problems early in the development cycle so reduce the costs. 
- Run the tests many times during development – easier to help with regression issues



### Aspects

- Unit interface
  - State after unit has been created
  - Setting and Getting data
  - Calling operations (e.g. methods in Java)

- Functional tests – black box

- Structural tests – white box

- Error handling

- Incorrect input



### Test Fixture

- Setup
  - Might create some common data to be used by several tests 
  -  Or… might just be local setup in each test method 

- Exercise – call methods on the SUT

- Verify (Assertions…) 

- Teardown (optional)



*use randomly generated values - not repeatable*



### Test Doubles

units that are used to replace a real parts of the system for test purposes, is used to simulate the modules that the SUT will interact with.

DOC: *Depended-on Component* 



### Test Driver Module

is used to exercise the SUT. It either receives data or loads tests. It runs those tests and collects the results. The results are then available for analysis.



### Relationship

![image-20201110233316410](assets/image-20201110233316410.png)



### Testing Strategies

- Top-down unit testing strategy
  - Test the top level first. Create test-doubles for units called by the top-level. Create driver for top-level. Then, use the tested unit as the driver for next level. 

- Bottom-up unit testing strategy
  - Test the bottom modules first. Create a driver module for it. When tested, move to next module up, creating a new driver. The tested lower-level module can be used instead of a stub. 

- Isolation testing 
  - Do not consider the relationship between modules. Design test doubles and driver for every unit.



### Types of Test Double

- Dummy Object
  - does not matter what value is actually in the data value, it just needs to exist
  - can be null sometimes

- Test Stub 
  - A unit that allows us to insert some logic to respond to calls from the SUT

- Mock Object 
  - An SUT needs to call methods in the DOC. We might want to confirm that the SUT works well.
  - A Mock Object is setup with information about what calls it should expect. It might also be setup with details of the data it should expect. 
  - A lot of unit testing is checking the state after an interaction. Mock Objects are testing the behaviour of the interaction between the SUT and DOC

- Fake Object
  - An object that replaces the functionality of the DOC



