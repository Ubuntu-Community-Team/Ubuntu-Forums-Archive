---
title: "Koctave with Ubuntu?"
date: 2007-05-13
forum: Education &amp; Science
---

### Post by merike on 2007-05-13
Installed, but when I launch I get:
"Octave path is not set, but found what seems to be Octave.
Will try to use usr/bin/octave."
After clicking OK nothing happens. Even the process in system monitor is killed.

---

### Post by merike on 2007-05-13
Apparently I needed kdebase.
But could somebody help me out with a simple three-dimensional plot? Like z(x,y)=x+y or similar. I've never used such a program before and tutorials I could find sounded too difficult.

---

### Post by tkjacobsen on 2007-05-13
x= 1:10;       
y= 1:10;
[X,Y]=meshgrid(x,y)
Z = X+Y;
mesh(x,y,Z)

---

### Post by merike on 2007-05-13
Thank you for the reply.

But how would I enter z^2=x^2+y^2?
Tried the same way but that gives an error.

---

### Post by tkjacobsen on 2007-05-13
> **merike said:**
> Thank you for the reply.

But how would I enter z^2=x^2+y^2?
Tried the same way but that gives an error.

You cannot do that. This is because octave is like a programming language. It is purely numeric and not algebraic.

A = B+C evaluates B+C and stores the result in A. if B and C are equally shaped vectors or matrices a will also be a vector or matrix of the same shape. That is what you are using here :
z=x+y, where x and y are both matrices.

You cannot have expressions on the left side of the = like
2*x = a+b <--- invalid.

So you would have to do:
x = linspace(-5,5,30);
y = linspace(-5,5,30);
[X,Y]=meshgrid(x,y);
Z1 = sqrt(X.^2 + Y.^2);
Z2 = -sqrt(X.^2 + Y.^2);       
mesh(x,y,Z1)
hold on
mesh(x,y,Z2)
hold off


%% Y.^2 means element-wise. Where Y^2 would be Y multiplied with Y (as in matrix multiplication.

---

### Post by merike on 2007-05-15
Thank you :)

---

