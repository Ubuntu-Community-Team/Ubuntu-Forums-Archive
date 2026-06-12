---
title: "math problem, can't seem to figure out the right answer"
date: 2011-05-19
forum: Education &amp; Science
---

### Post by Chewey56 on 2011-05-19
**heres a math problem that i've been working on, for some reason i can't get the right answer.**

What is the smallest positive zero of function f(x) = 1/2 - sin(3x + Pi/3)? 

A) Pi 
B) Pi/3 
C) Pi/6 
D) Pi/18 
E) Pi/36

Here's what i have tried:
```
since the problem is asking for a zero, then i set the equation equal to 0 and added the sine equation to each side to get:
1/2 = sin(3x+pi/3)

Then, i did the cosecant of each side, or on a TI-83 calculator it would be recognized as sin with a superscript -1, denoting and inverse of sine.

30 = 3x+pi/3

Then, i converted the pi/3 into degrees, which comes out to be 180/3 or 60.

30 = 3x+60

Subtracted 60 from each side.

-30 = 3x

divide by 3 and get:

x = -10

convert back into pi radians

x = -pi/18
```

The answer is said to be c, which works out when plugged into the equation. i just don't see how to get to said conclusion. anybody interested?

---

### Post by Graham-W on 2011-05-19
Why are you asking this on UbuntuForums? I'm sure there's other places to post your question.
If I'm coming off as mean, sorry; I know your pain. Try some other forum group.

---

### Post by Chewey56 on 2011-05-19
> **Graham-W said:**
> Why are you asking this on UbuntuForums? I'm sure there's other places to post your question.
If I'm coming off as mean, sorry; I know your pain. Try some other forum group.

most of the people on here are proficient in computer programming, which almost goes hand in hand with mathematics. and this forum *IS* titled Education and Science, so i thought that it would be fitting to post here.

---

### Post by khauenst on 2011-05-19
You also need convert the 3x to degrees by multiplying it by (180/pi)

---

### Post by dorothykinder on 2011-05-20
Do feel that you are correct with your answer.. i applied the same method.. Pi/18 is teh correct answer.

---

### Post by Azrael3000 on 2011-05-20
Nah guys. It's asking for the smallest positive zero and your calculation in the original post is correct but you have x = -pi/18 which clearly is negative. So where are you wrong?
Look at this pic: [https://secure.wikimedia.org/wikipedia/en/wiki/File:Unit_circle_angles_color.svg](https://secure.wikimedia.org/wikipedia/en/wiki/File:Unit_circle_angles_color.svg)
and figure out at which angles x, sin(x) = 1/2. Once you found the other value do the calculation you did originally et voila.

---

### Post by dwhite on 2011-05-21
the answer is c as you suggest x=pi/6, i've attached a plot of the function showing the roots x=-pi/18, x=...  As suggested by Azrael3000 the first solution is arrived at assuming arcsin(.5)=pi/6, but there is another solution to arcsin(.5) between 0 and 2*pi find it and you shall have the answer c :)

the problem with most calculators is that they are programmed to give you only one solution for an angle (typically whichever is in the first or fourth quadrant) but this can lead one to not consider other possible solutions.

---

### Post by madmathigan on 2011-05-21
My Pre-Calc students made a similar incorrect assumption.  Sine can only be canceled out by taking the arcsin.  You cannot use secant to cancel out sine.  You have to take the arcin.  Your first step was fine.  Now, to cancel out sin, take arcsin of 1/2.  To do that, look at your unit circle and see where the y-value is 1/2.  That gives you 30 and 150, or pi/6 and 5pi/6.  What's smaller?  pi/6.

---

### Post by dwhite on 2011-05-21
> **madmathigan said:**
> What's smaller?  pi/6.

but use the 5pi/6 value for the angle to give you the first positive value for x

---

### Post by madmathigan on 2011-05-22
> **dwhite said:**
> but use the 5pi/6 value for the angle to give you the first positive value for x

Nope.  If you solve it algebraically:

5pi/6 = 3x + pi/6
4pi/6 = 3x
2pi/3 = 3x
2pi/9 = x

When you plug 2pi/9 into a calculator and round, you get (after rounding) the point (.7, 0).  So, at .7, roughly, you have a zero.  If you plug in pi/6:

pi/6 = 3x + pi/6
0 = 3x
0 = x

Plug it in and you get the point (0,0), which means that you have a positive root there.  (It's positive because 0 is neither positive nor negative, so we consider 0 to be not negative.)  Therefore, pi/6 is the smallest positive root.

---

### Post by dwhite on 2011-05-22
> **Chewey56 said:**
> **heres a math problem that i've been working on, for some reason i can't get the right answer.**

What is the smallest positive zero of function f(x) = 1/2 - sin(3x + Pi/3)? 

  

that's the original problem, the solution by madmathigan assumes a different function

> **madmathigan said:**
> Nope.  If you solve it algebraically:

5pi/6 = 3x + pi/6     <---should be 3x+pi/3
4pi/6 = 3x
2pi/3 = 3x
2pi/9 = x



to solve the original problem use arcsin(.5) = 5pi/6  (if you use arcsin(.5)=pi/6 you will get the root -pi/18 as shown on the plot posted earlier)



PS
pi/6 is not a root to the problem solved by madmathigan ... the root corresponding to arcsin(.5)=pi/6 is 0 in that problem

attached is a plot showing both the function proposed by Chewey56 in red and that solved by madmathigan in blue (showning the root at 0)

---

### Post by BelmontHarry on 2011-06-03
I think You also need convert the 3x to degrees by multiplying it by (180/pi).

---

### Post by hal8000 on 2011-06-08
> **dwhite said:**
> 
PS
pi/6 is not a root to the problem solved by madmathigan ... the root corresponding to arcsin(.5)=pi/6 is 0 in that problem

attached is a plot showing both the function proposed by Chewey56 in red and that solved by madmathigan in blue (showning the root at 0)

A very nice plot, may I ask what program was used to produce the plot?

---

