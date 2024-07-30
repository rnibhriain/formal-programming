# Formal Programming

2023 - 2024

All assignments for module: CA648

## Assignment One
### Question 1
A primary school class contains a number of children and a variety of books. Write a model which keeps track of the books that the children have read. It should maintain a relation hasread between children and books. It should also handle the following events:

record: adds the fact that the given child has read the given book

newbook: outputs a book that the given child has not already read

books_query: outputs the number of books the given child has read


### Question 2
A club membership department maintains a set of members, and a set of people that are in the waiting list to become members. No member can also be waiting for membership. The club allows a maximum of 500 members at any one time.

Using the set NAMES, and the variables member and waiting to maintain the required information, write suitable invariants that capture the constraints on these variables.

The model should handle the following events:

join: the given name, which must be in the waiting list, is made a member and removed from the waiting list

join_queue: the given name, which must not be in the waiting or membership lists, is added to the waiting list

remove: the given name, which must be in the membership list, is removed from the membership list

remove_queue: the given name, which must be in the waiting list, is removed from the waiting list

jump_queue: the given name, which must not be in the waiting or membership lists, is made a member

query_membership: outputs the number of members

query_queue: outputs the number of people in the waiting list.


### Question 3
A parking permit management system keeps track of people that have had parking permits registered to them. Each person with a permit must have exactly one car registered, and different people must register different cars. Write a model which maintains this information. It should handle the following events:

register: registers the given vehicle for the given person, provided they do not already have a vehicle registered

deregister: deregisters the vehicle for the given person

registered: outputs yes if the given person has a car registered and no otherwise

vehicle: outputs the vehicle that the given person has registered

owner: outputs the owner of the given vehicle

change_register: changes the vehicle that the given person has registered to the given vehicle

drugs_check: outputs a random registered vehicle to search for drugs.

In order to provide outputs for registered, you will need to provide a set RESPONSE which contains at least the elements yes and no.


### Question 4
Students are examined in a particular course with a pass mark of pass_mark, where marks are between 0 and 100. They may resit the exam up to twice more if they fail. In such cases the maximum mark allowed is the pass mark.

Write a model which tracks the examination results associated with the particular course. It will maintain a set registered which contains all of the students who have ever been registered for the course, and three functions: exam, resit1, and resit2. These contain the results of registered students. They should maintain information in a sensible way: for example, only registered students should have any marks; a student cannot have a resit1 mark unless they also have an exam mark; and if a student has a pass mark on the exam then they cannot have a resit1 mark. Write suitable invariants that express these constraints.

The model should handle the following events:

register: registers the given unregistered student for the course

exam_mark: enters the given exam mark for the given student

resit1_mark: enters the given first resit mark for the given student

resit2_mark: enters the given second resit mark for the given student

studentquery: outputs how many times the given student has sat the exam

markquery: outputs the top mark that the given student has achieved in any of the sittings of the exam

## Assignment Two

### Question 1
In the project Progress.zip, the machine Progress tracks the career progress of employees, by partitioning them into three sets. It should be refined to maintain a partial function from employees to their employment status as described in the template ProgressR.

### Question 2
In the project Papers.zip, refine the machine Papers so that the set of houses is maintained by a partial function as described in the template PapersR.

### Question 3
A stack is a last-in-first-out queue, which allows elements to be pushed onto the top of the stack, or popped from the top of the stack. Such a stack is specified in the project Stack.zip in the machine Stack. You should give a refinement for this machine. Your refinement should use an array to record the elements of the stack in order.

### Question 4
In the project Buffer.zip, provide a refinement of the machine Buffer, which implements a first-in-first-out queue.

You should achieve this by using an array a : 1..maxsize +-> ELEMENT to keep track of the contents of the buffer. You will also need some other state variables: f, to keep track of the next element to be output, b, to keep track of the point beyond the end of the buffer (i.e. where the next input will be placed), and you should also track the number of elements in the buffer. The contents of the buffer will correspond to the elements of the array between f and b (allowing for wrap-around if b < f because of arithmetic modulo maxsize). For example, with maxsize = 10, the buffer containing 3, 5, 4 and 8 may correspond to the array [0,0,0,0,3,5,4,8,0,0] with f = 5 and b = 9. It may also be represented by [4,8,0,0,0,0,0,0,3,5] with f = 9 and b = 3.

The linking invariant will thus link buffer and a as follows: !n.(n:dom(buffer) => buffer(n)=a((n mod maxsize)+1))
