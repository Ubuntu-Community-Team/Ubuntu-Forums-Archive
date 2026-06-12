---
title: "Python, SciPy and graphics"
date: 2008-05-23
forum: Education &amp; Science
---

### Post by Stochastics on 2008-05-23
Hi,

I'm trying to learn the Python language for scientific purpose. It appears there are a lot of different package for scientific graphics (both 2D and 3D). My question is : What is the best one available ? And, if anyone know where i can find a tutorial/reference of the NumPy package, it would be great too !
Is there any specialized scientific Python forums out there ?

Thanks !

---

### Post by crmccreary on 2008-07-20
Travis Oliphant, the author of the numpy package and it's predecessor, numeric, publishes numpy documentation in a pdf format. It's not free, though.

You should try scipy.org and enthought.com (chaco, mayavi) for advice and examples of scientific visulaization.

---

### Post by tamoneya on 2008-07-20
take a look at sage: [http://www.sagemath.org/](http://www.sagemath.org/)

It is basically a compilation of python packages and a nice interface.

---

### Post by ssam on 2008-07-23
i am using numpy and matplot lib to do lots of calculations and 2d plotting.

[http://matplotlib.sourceforge.net/screenshots.html](http://matplotlib.sourceforge.net/screenshots.html) shows the kind of stuff it is capable of.

---

### Post by iopo on 2008-07-23
Hi!
I'm not an expert, but what I know I learned here:

for Python
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)
(there is a lot of stuff. I guess what you really need are three things: an overview on different type pf data, control flow statements -if, for, while- and how to use and define functions)

for Numpy
[http://www.scipy.org/Tentative_NumPy_Tutorial](http://www.scipy.org/Tentative_NumPy_Tutorial)

for Scipy
[http://www.rexx.com/~dkuhlman/scipy_course_01.html](http://www.rexx.com/~dkuhlman/scipy_course_01.html)
(but there is no point in studying it from top down. Scipy is basically a collection of functions. Whenever you think you need something you can look it up)

For plotting I use Matplotlib
[http://matplotlib.sourceforge.net/](http://matplotlib.sourceforge.net/)

Then,if you are stuck with something you can try with google: there are many more resources out there.

Best

---

### Post by Frenske on 2008-09-08
I have just started using python for scientific purposes. I have started with Sage, but I did not like it. Too much focused on mathematical algebra rather than numerical computations. I am sure I can do the same with Sage as I do now, but it was a typical 'Can't see the forest through the trees' and I only installed what I needed: numpy, scipy, matlibplot and the native python editor is replaced by ipython.

When you are familiar with python and the other libraries you should have a look at pypy to streamline your code and maybe freeze to create executables in Linux.

---

### Post by iQuizzle on 2008-12-16
for python, learning the **numpy** package is a must. the best graphical package i found was matplot by a long shot. i've never done much in 3d, but for 2d stuff it literally has everything...and you can easily embed it in gui applications.

of course, you can use any plotting package that you can call from the command line by importing the standard os module and calling os.system.

---

### Post by ssam on 2008-12-17
the numpy book is free (public domain) now. [http://www.tramy.us/](http://www.tramy.us/)

---

