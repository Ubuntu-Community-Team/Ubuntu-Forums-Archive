---
title: "3D Plotters - programming output"
date: 2008-08-11
forum: Education &amp; Science
---

### Post by lordhaworth on 2008-08-11
Hey all

I've written a really simple simulation - the output of which is a list of trajectories (in cartesian coords) and a corresponding wavelength (Programming in Fortran90). Does anyone know of a good 3D graph plotter so i can visually represent this output - if possible where i can alter the colour of the trajectory depending on the wavelength? 

Cheers

Tom

---

### Post by stumbleUpon on 2008-09-17
You could write a simple shell script (or a subroutine in F90 itself) to produce povray ([http://www.povray.org](http://www.povray.org)) files and then render the images.

There is a lot of flexibility in controlling color, texture ...etc

---

### Post by slaanco on 2008-09-19
try [VisIt]("https://wci.llnl.gov/codes/visit/")

---

### Post by kaspar_silas on 2008-09-23
I have two options for you. The easy road to a perfectly acceptable solution and the tough road to the perfect solution. Both options are more than capable of exactly what you want.

Firstly there is the very simple gnuplot 
[http://www.gnuplot.info/]("http://www.gnuplot.info/")
which is very easy to use and probably the one I would recommend. Plus as you are generating your trajectories you can call gnuplot and plot it as you go. 

Secondly there is OpenDX. 
[http://www.opendx.org/]("http://www.opendx.org/")
This is the mother of scientific data visualization software. It can produce amazingly pretty plots of pretty much any type. However in my experience it has a learning curve like a rockets trajectory. However once mastered you will not need anything else.

---

