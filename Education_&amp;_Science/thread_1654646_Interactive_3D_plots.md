---
title: "Interactive 3D plots"
date: 2010-12-28
forum: Education &amp; Science
---

### Post by schievelbein on 2010-12-28
I am starting to work on a project and cannot find the software that I need.
I have a massive amount of 3D spatial data in spreadsheets that could be put into a database if needed.  This data are coordinated for vertices of 3d objects.  I need to manipulate the data and see the results in real time.  I do not know if there is a single program that will handle this or if I need multiple programs.  I know that there are programs that will plot the data and allow me to manipulate the 3D object, but I do not need that, I need to work on the data itself.

A more detailed explanation is that I need a 3D State Model Engine.  I need to be able to set the position of the objects in 3D space, and as I change the state of one object, I need to know how it will affect the other objects.  I can program most of this using trigger effects in spreadsheets, so that as one cell changes, it changes the other cells.

An example of this is to think of 3 spheres sitting side by side with magnetic fields on each sphere.  As I rotate any one sphere, it will cause the other spheres to rotate dependent on the field strengths.  This is NOT a one-to-one like gears, but analog influence.  To make matters worse, this is in 3D space.  If I rotate along X-axis, it affects the surrounding objects in one way, Y-axis different objects, and Z-axis different objects.  

I would prefer to use my Ubuntu powerhouse system, but if needed, I could also install windowz or use wine..... 

Any suggest and/or comments are welcome.
I can do simple programming using Python or similar if needed.
I have surfed MANY hours and I am at a total loss as to where to proceed.

Thank You
Michael

---

### Post by Marlonsm on 2010-12-28
I'm also looking for something like this.
In a quick search I've found this:
[http://scipy.org/Cookbook/Matplotlib/mplot3D](http://scipy.org/Cookbook/Matplotlib/mplot3D)
I didn't try it yet and still don't know how do I get it to work.
It works with Python and uses some modules.

I think you'd need to export all that data to a text file, get python to read it and get the points, then plot it with one of those codes.

For me, I already have my data in text files, I want to try it either later today or tomorrow, I'll post back here if I have any success.

EDIT: I also found this: [http://en.wikipedia.org/wiki/Matplotlib](http://en.wikipedia.org/wiki/Matplotlib)

EDIT2: I got the basics working, after downloading and installing the matplotlib, I made a program to get all the x,y,z coordinates into lists and I used the "scatter" plotting, found on that first link.
The result is not what I want yet, but that's a start. It plotted all points in the order they appeared in the file, making a line between them, and the x,y,z axes are not in scale as I want.

---

### Post by kaspar_silas on 2011-01-18
Hey,

Check out processing. Its a simple graphics based language. It was initially designed for interaction and for use by artists and non programmers. Hence its a doodle to learn.

However its initially hidden java core is actually quite powerful and easy to expand. The slightest bit of programming experience and you should be going in an hour on so if you don't get distracted by the examples.

I wrote an interactive solar system to play planet pool once. That's why your question reminded me of it. Anyway It sounds perfect for you.

 Its available at [www.processing.org](www.processing.org)

Enjoy

---

### Post by Marlonsm on 2011-01-19
Thank you!
That processing seems to be just what I needed.

---

