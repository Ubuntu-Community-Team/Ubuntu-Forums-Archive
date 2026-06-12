---
title: "Program C help"
date: 2008-02-04
forum: Education &amp; Science
---

### Post by Orkinman34 on 2008-02-04
Hello, 

I'm in dire need of help for computer program C. Could someone please help me?

Problem 1:

Write a program which reads three integer values and orders them.The program will then print them in ascending order
(smallest integer first) and state if there are duplicate inputs.
When executed, if there are no duplicate inputs your program’s output should be as follows:
Please enter integer #1 : 4
Please enter integer #2 : -5
Please enter integer #3 : 10
Output Message: -5 4 10 No duplicates found.
On the other hand, if there are duplicate inputs your program’s output should be as follows:
Please enter integer #1 : 2
Please enter intefer #2 : 4
Please enter integer #3 : 2
Output Message: 2 2 4 Duplicates found.

Problem 2

The factorial of a nonnegative integer n is written n! and is defined as follows:
n! =

n ·(n&#8722;1) ·(n&#8722;2) ···1 if n > 0
1 if n = 0
Examples of 5!, 4! and 3! are as follows:
5! = 5 ·4 ·3 ·2 ·1 = 120
4! = 4 ·3 ·2 ·1 = 24
3! = 3 ·2 ·1 = 6
1
Write a program that reads an integer and computes and prints its factorial. If the input is a negative integer let the user
know that the factorial function only works for nonnegative integers. Note: Your program execution terminates only
when 0 is entered. In other words, your program should allow an arbitrary number of integers to be entered. When
executed, your program’s output should be as follows:
Please enter an integer (0 to exit): 4
Output Message: The factorial is: 24. Try another(0 to exit): 0
Output Message: Bye.
On the other hand, if the input is a negative number the output should be as follows:
Please enter an integer (0 to exit): -2
Output Message: Factorial only works for nonnegative integers.
Please try again(0 to exit): 5
Output Message: The factorial is: 120. Try another (0 to exit): 4
Output Message: The factorial is: 24. Try another (0 to exit): ..
.
.
.
Output Message: Bye.

Problem 3

Write a program that reads five positive integers from the user input. The program will then compute a matrix of ratios
of each of the five integers’ factorial compared to themselves and to the other integer’s factorial. You might want to
use the factorial computation code that you developed in problem number 2. Note: Given two positive integers x and
y: The ratio of x compared to y is x/y. The ratio of x compared to x is x/x=1. Please keep in mind that the result of
the division of two integers might result in a floating point value and it must be printed as such. Also keep in mind
that the factorial of 0 is 1 and therefore there will not be division by zero in this problem. The output should be of the
following form:
INTEGER 1 INTEGER 2 INTEGER 3 INTEGER 4 INTEGER 5
INTEGER 1 1 ratio ratio ratio ratio
INTEGER 2 ratio 1 ratio ratio ratio
INTEGER 3 ratio ratio 1 ratio ratio
INTEGER 4 ratio ratio ratio 1 ratio
INTEGER 5 ratio ratio ratio ratio 1


[https://eee.uci.edu/08w/18010/assignment3.pdf](https://eee.uci.edu/08w/18010/assignment3.pdf)

Thank you so much

---

### Post by Crinos512 on 2008-02-04
Ah, this really takes me back..... :)

Computer Science was always such a great subject for me because it really got those creative juices flowing and brain cells tingling.



Please don't cheapen my acheivement by asking someone to rob you of the experiance.
(If Computer Science doesn't suit you you can always try for an MIS Degree...)

---

### Post by DrMega on 2008-02-04
Would this be for a school/college assignment by any chance? It looks a lot like a practical assignment. That being the case, if we write it for you it would not help you with your course. Why don't you have a good crack at it and then post up if you get stuck.

---

### Post by Orkinman34 on 2008-02-04
Actually im a chemical engineer and every engineer is required to take this class, but so far the first problem is taking me forever to do. i keep on getting stuck on the if statements

---

### Post by Orkinman34 on 2008-02-04
#include<stdio.h>
int main()

{

int i1, i2, i3;
int temp;


printf("Please enter integer i1: ");
scanf("%d", &i1);
printf("Please enter integer i2: ");
scanf("%d", &i2);
printf("Please enter integer i3: ");
scanf("%d", &i3);

if (i1 < i2 && i1 < i3)
if (i2 < i3)
{ printf("No duplicates found\n",i1,i2,i3); }
else if (i2 < i3)
if (i1 < i3)
{ printf("No duplicates found\n",i2,i1,i3); }
else
{ printf("No duplicates found\n",i2,i3,i1); }
else
{ printf("No duplicates found\n",i3,i2,i1); }
if (i1 <= i2 && i1 <= i3)
if (i2 <= i3)
{ printf("Duplicates found\n",i1,i2,i3); }
else
{ printf("Duplicates found\n",i1,i3,i2); }
else if (i2 <= i1 && i2 <= i3)
if (i1 <= i3)
{ printf("Duplicates found\n",i2,i1,i3); }
else
{ printf("Duplicates found\n",i2,i3,i1); }
else if (i1 <= i2)
{ printf("Duplicates found\n",i3,i1,i2); }
else
{ printf("Duplicates found\n",i3,i2,i1); }

printf("Output Message: %d\t%d\t%d\n", i1,i2,i3);

return 0;

---

### Post by LaRoza on 2008-02-04
[color="red"]Acting as moderator:[/color]

We don't do assignments here, ask you instructor for help.

---

