---
title: "Ubuntu in Aerospace"
date: 2007-07-12
forum: Education &amp; Science
---

### Post by Icarosaurus on 2007-07-12
Hello all,
I decided to start this thread to share informations on useful software for the aerospace engineering community (first of all student and researchers). I'll start with a list of useful programs, to be updated  time by time:

**Xfoil**
[URL="http://web.mit.edu/drela/Public/web/xfoil/"]http://web.mit.edu/drela/Public/web/xfoil/
[/URL]

**GNUPlot**
[http://www.gnuplot.info/]("http://www.gnuplot.info/")
Available in the Ubuntu Repository


Feel free to suggest links, programs, tips and whatever you think to be useful!

---

### Post by elfstone214 on 2007-07-13
subscribed! :D

---

### Post by Icarosaurus on 2007-07-20
So... nothing to put on the table?

---

### Post by jk3 on 2008-12-23
Hey
[B]
AVL[/B]
"AVL is a program for the aerodynamic and flight-dynamic analysis of rigid aircraft of arbitrary configuration. It employs an extended vortex lattice model for the lifting surfaces, together with a slender-body model for fuselages and nacelles."
[REF:[http://web.mit.edu/drela/Public/web/avl/]](http://web.mit.edu/drela/Public/web/avl/])

It was also created by prof Drela and the source code is available from a similar location to Xfoil ( [http://web.mit.edu/drela/Public/web/avl/](http://web.mit.edu/drela/Public/web/avl/)). 

As with Xfoil, AVL compilation process requires modification of Makefiles to match system. However, the process is less involved than Xfoil and seemed to work with little editing on a 32 bit Ubuntu Ibex setup (gfortran compiler used and package set up for single precision)

**Mises** 

Another package from Prof Drela, Mises is an Euler/coupled BL solver for aerofoil cascade analysis (gas turbines). Mises is not available on MIT public pages, but can be obtained from MIT contacts directly free of cost. I have a copy of the source files for the latest version, but would prefer not to share directly if possible (better to go through the correct routes in order to obtain Mises)


Icarosaurus, thanks for setting up this thread and for the description of Xfoil install. I am currently attempting to install Xfoil on this machine (following instructions in thread [http://ubuntuforums.org/showthread.php?t=994912](http://ubuntuforums.org/showthread.php?t=994912) ) but have not managed to sucessfully complete the installation. I would appreciate advice on Xfoil install, but will give details on the other thread.

---

### Post by cdnaerogeek on 2009-01-09
Hi,

Small thread, but we can change that fairly quickly. 

My most commonly used computer language is [**Python**]("http://www.python.org/"). In our lab, we use it for basically everything. With the [Numpy and Scipy]("http://www.scipy.org/") extentions, and the [matplotlib]("http://matplotlib.sourceforge.net/") plotting extensions, you basically get the most commonly used bits of MATLAB for free. Everything is available in the Ubuntu repositories.

Cheers.

---

### Post by Icarosaurus on 2009-01-20
> **jk3 said:**
> 
Icarosaurus, thanks for setting up this thread and for the description of Xfoil install. I am currently attempting to install Xfoil on this machine (following instructions in thread [http://ubuntuforums.org/showthread.php?t=994912](http://ubuntuforums.org/showthread.php?t=994912) ) but have not managed to sucessfully complete the installation. I would appreciate advice on Xfoil install, but will give details on the other thread.

I'll make a 64 bit package as soon as I can.
In the meanwhile, you can go to my thread and follow the instructions for making the 32 bit version work in a 64 bit environment.
[URL="http://ubuntuforums.org/showthread.php?t=288920"]http://ubuntuforums.org/showthread.php?t=288920
[/URL]

---

### Post by openae on 2010-01-05
Just to let you know that MISES has been labeled as a commercial product by Mark Drela and MIT, so there is no chance that will be able to get your hands on it.  

Also check out [http://openae.org](http://openae.org) ...we specialize in all of this stuff ;)

---

### Post by not_a_phd on 2010-01-08
Here are a couple more:

**octave** ( [www.octave.org]("http://www.octave.org") ) GNU Octave is a high-level language, primarily intended for numerical computations.  It provides a convenient command line interface for solving linear and nonlinear problems numerically, and for performing other numerical experiments using a language that is mostly compatible with Matlab. It may also be used as a batch-oriented language.

**g77** - you know what I'm talking about!! Can't compile my digital datcom without it ;-)

**FlightGear** ( [www.flightgear.org](www.flightgear.org) ) see it to believe it. Not just a game.

---

### Post by Neezer on 2010-01-09
When I was in school a few years ago I took an automated controls class. Our final project was to design an autopilot to land a 747 in a cross wind.....We used MATLAB with Simulink. Is there an open source 'simulink' available at all? 

It was a great way to graphically represent control diagrams and differential equations.

---

### Post by openae on 2010-01-13
YES, there is! You can use SciLab with a controls component (plugin).

You can download SciLab here: [http://www.scilab.org/](http://www.scilab.org/)
And the popular controls plugins here: [http://www.scilab.org/contrib/index_contrib.php?page=download](http://www.scilab.org/contrib/index_contrib.php?page=download)

Also, if you have second, register at openAE and write an article about any of this, we would REALLY appreciate it...plus you get published.

Good luck!


> **Neezer said:**
> When I was in school a few years ago I took an automated controls class. Our final project was to design an autopilot to land a 747 in a cross wind.....We used MATLAB with Simulink. Is there an open source 'simulink' available at all? 

It was a great way to graphically represent control diagrams and differential equations.

---

### Post by openae on 2010-01-17
I got a chance to compile AVL for 32/64 bit machines as well as QPROP/QMILL for 64 bit computers yesterday.

You can find all these binaries at [http://openae.org/downloads](http://openae.org/downloads)

I especially encourage you to take a look at AVL, as it is used often in the industry.

---

