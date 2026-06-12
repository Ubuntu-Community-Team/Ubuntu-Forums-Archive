---
title: "How to graph two functions with respect to each other?"
date: 2010-12-07
forum: Education &amp; Science
---

### Post by M. Amin on 2010-12-07
Hello,

I'm new to math software. we all know how to graph f(x) vs. x; but what if I want to draw f(x) vs. g(x) for instance. How is that possible?
And another question, how to superimpose two functions on the same graph sheet?

I have installed wxMaxima and QtOctave. Feel free to suggest other software you think is good.

Thanks in advance.

---

### Post by surfer on 2010-12-07
gnuplot is surely worth a shot.

and if you need a full-blown math package, i use and recommend [sage]("http://www.sagemath.org/").

---

### Post by hubie on 2010-12-07
I can't help you with wxMaxima or QtOctave, but here is how to do it using R.  Here is a sample script (it is actually only a few lines long, but I commented the heck out of it to help you get started):

```
# This will plot f(x) vs g(x)
# Define x from 0 to pi in 100 steps
x <- pi*seq(0,1,by=0.01)
# Define first function f(x) as, say, e^x
f <- exp(x)
# Define g(x) as sin(2*x)
g <- sin(2*x)
# Plot them
plot(g, f, pch=16, col='blue')
title("Plot of exp(x) vs sin(2x) from 0 to Pi")
```

Now to plot them on the same plot:

```
# first plot f and set the plot limits to make sure you get them
# both on the same plot
plot(x, f, pch=16, col='blue', ylim=c(min(g), max(f)))
# overplot g
points(x, g, pch=16, col='red')

```

---

### Post by Harsh Kumar Narula on 2010-12-08
I can tell you how to do that in octave. Since you have Qtoctave installed at your system so I am assuming octave is already there. Suppose you have g(x) to be plotted against f(x). I mean f(x) on the horizontal axis and g(x) on the verticl axis.  
 
Say f(x) = X^2;
and g(x) = 2*X;
-1<= x <= +1 ;
 
I am writing the octave code here. 
%-------------------------------Start Copying from Here-----------------------------------------%
 
**X = -1:0.001:+1;** 
 
% This will make X vector with first element -1 and the last to be +1. Common 
%difference in two successive elements being 0.001. So the parameter 
%meshing/discretization is fine enough.
 
**F = X.^2;** % this will create dicretized F vector, *f(x) actually*;
**G = 2*X;** % this will create dicretized G vector, *g(x) actually* ;
 
 
**plot(F,G); %** This will plot F on horizintal axis vs G on Vertical axis 
 
**grid on;** % In case you want to show the grids
**title('F vs G');** % In case you want a title of the graph
**xlabel('HorizontalLabel');** % In case you want a label on horozintal axis
**ylabel('VerticalLabel');** % In case you want a label on vertical axis
 
%------------------------ Program Ends----------------------------------------------------%
 
Copy and paste it in ur fovourite text editor and save it at your favourite place (say Desktop); This file name should have extention *.m. Suppose you save it as _arbit.m. _*
 
Now open a terminal, type 
*cd Desktop*
 
then type
*octave*
 
then type
*arbit* 
 
This will give you the desired plot. I hope it will help you. Octave is an excellent mathematical tool and easy to understand; just try your hands on it.
 
P.S.~ The bold lines in this post are enough for octave to understand it. Comments after %sign are written just to explain you. Though you can copy and paste with comments, which will not harm. You can see output of my octave in the attachment. 
For increasing the font size of xlabel, ylabel and title just google it. Dude did you expect a parabola here ? Remind (at^2,2at) !!! :P

---

### Post by M. Amin on 2010-12-08
Thank you a lot guys that was helpful :)

---

