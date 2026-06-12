---
title: "QtiPlot or other plotting software: how to assign symbol/marker style to a number?"
date: 2014-02-26
forum: Education &amp; Science
---

### Post by zircon_34 on 2014-02-26
I am new to linux and the only barrier for using it in my everyday work is a scientific plotting software for publication quality plots. I am looking for something similar to Sigmaplot or Grapher, but for free.

I just tried out QtiPlot. A features I could not find was to assign a symbol/marker style to a number. 

Example I have a spreadsheet with three columns x y z. x and y would be my data for a 2-D scatter plot and z would contain a number (e.g., 1, 2 and 3) that could assign to each of my x-y pairs a specific marker type or marker color (e.g. 1= filled circle, 2= star and 3= square).

Does anyone use scientific software for plotting lots of data and managed to do this type of plot in QtiPlot?

Any help appreciated, also suggestions of other scientific plotting software I may have missed...

---

### Post by 23dornot23d on 2014-02-27
Matplotlib and small programs written in python may give you what you need

Here is a search I did on what you requested ......

[https://www.google.co.uk/search?q=assign+a+symbol/marker&client=ubuntu&hs=HpP&channel=fs&source=lnms&tbm=isch&sa=X&q=linux+python+assign+a+symbol+marker+matplotlib&tbm=isch](https://www.google.co.uk/search?q=assign+a+symbol/marker&client=ubuntu&hs=HpP&channel=fs&source=lnms&tbm=isch&sa=X&q=linux+python+assign+a+symbol+marker+matplotlib&tbm=isch)

I have only done small programs and whether they meet your specifications for high quality - that is something only you
will be able to tell by knowing what it is that you require and then by seeing what you can obtain for free.

---

### Post by mdshaver81 on 2014-02-27
You should really check out Veusz.
[http://home.gna.org/veusz/](http://home.gna.org/veusz/)
It is in the repos with updates available via a PPA which can be found on the Veusz website.

---

### Post by zircon_34 on 2014-02-28
Alright, thanks for the links! Its in my list, I will try those out.

---

### Post by zircon_34 on 2014-02-28
> **23dornot23d said:**
> Matplotlib and small programs written in python may give you what you need


I actually never thought of using python (learned a bit of C++ in the past), but just checked out some tutorial, seems I am going to give it a try  :popcorn: do you use python-scitools with Matplotlib, which packages could you recommend for download?


> **23dornot23d said:**
> I have only done small programs and whether they meet your specifications for high quality - that is something only you
will be able to tell by knowing what it is that you require and then by seeing what you can obtain for free.

Nothing fancy, I just meant no plot like in excel. Just plain white background, customizable axis, standard symbols (square, circles, star, etc...), easy clonable graphs. I use pdf or eps format. More like 2-D plots done in GnuPlot but I prefer a GUI to have the work done with spreadsheets and datahandling of many data. I also need sometime to do ternary diagrams, apparently veusz is capable of doing that and has a nice GUI!

I still have to try the marker styles (title of the thread) in the two different programs! but many thanks for the recommendations!

---

### Post by 23dornot23d on 2014-03-01
This is a quote from the methods used in the below link .......... but allows for style to be matched to a line or marker .........

I think that this is what you may be after ..... how difficult it will be to set up compared to graphing programs that do most
things automatically may be the time consuming part ...........

The method pylab.savefig(FILENAME.FMT). The .FMT can be one of several, e.g., .eps, .svg, .ps, .pdf, .png, .gif, .jpg, etc.). Some of these (the vector graphics ones like pdf, ps, eps and svg) can be opened in Adobe Illustrator for modification. 

   As mentioned earlier, if you give plot() a single sequence of values, it assumes they are y values and supplies the x values for you. Garbage in, garbage out. But plot() takes an arbitrary number of arguments of the form: (X[SUB]1[/SUB],Y [SUB]1[/SUB],[COLOR=#ff0000]** line_style_1**[/COLOR], X[SUB]2[/SUB],Y [SUB]2[/SUB],[COLOR=#ff0000]** line_style_2**[/COLOR], etc.), where &#8217;line_style&#8217; is a string that specifies the line style as illustrated in this script called matplotlib2.py                                                                                                                                                 

[http://earthref.org/PmagPy/cookbook/](http://earthref.org/PmagPy/cookbook/)

_____________________________________________________________________________________
A simple test to make sure you can get matplotlib working on your own system is here for the pi
but its got some good explanations to get the basics going. 
( if you have problems at all then I have a small script that I run to cover a lot of the dependencies for getting graphs to work )

Here is the basic minimal install I do on each of my systems - but make sure it suits yours
with aptitude warnings are given for dependencies and answering no may give better options
sometimes upgrading packages rather than removing anything ......
 ( I usually avoid removals unless I can see its giving me a later replacement )

```

#!/bin/bash
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install python-matplotlib
sudo aptitude install tk
sudo aptitude install python-gtk2-dev
sudo aptitude install python-pygame
sudo aptitude install python-qt4-dev
sudo aptitude install libqglviewer-qt4-dev
sudo aptitude install python-vtk
sudo aptitude install python-pip
sudo pip install visvis
sudo pip install visvis --upgrade
sudo pip install mayavi
sudo aptitude install python-tk
sudo aptitude install pyqt4-dev-tools
sudo aptitude install libfltk1.3-dev
# takes a long time to build this last one ... uncomment if needed
# sudo pip install pyside
# better way to do this
sudo aptitude install pyside-tools
sudo aptitude install python-wxtools
sudo aptitude install python-opengl


```

[http://www3.telus.net/danpeirce/notes/matplotlib.html](http://www3.telus.net/danpeirce/notes/matplotlib.html)

---

### Post by zircon_34 on 2014-03-01
Thanks for the package list!

Just for those scientists that never used python or matplot lib the links for basic information:

[http://python.org/](http://python.org/)   #for python programming language
[http://matplotlib.org/](http://matplotlib.org/)  #for documentation about matplotlib

python is installed by default in ubuntu and OSX. Then the first thing to install is: idle-python3.3 (for python 3) to learn the basics.

---

### Post by zircon_34 on 2014-03-02
Ok thread solved:D, also tried Veusz, there you can set marker styles and colors based on a number in a column! and its also based on python and versatile!

Whats great in this forum, is that you come up with a problem and people make you explore sometime other fun possibilites! I just see that the approach here (linux) is different, and people try to adapt the software to their needs, rather than to adapt their needs to the software. 

I just discovered Ipython notebook, its quite enjoyable to learn python for scientific computing, here is the link:

[http://ipython.org/ipython-doc/stable/interactive/notebook.html](http://ipython.org/ipython-doc/stable/interactive/notebook.html)

Just had one problem trying Veusz, when importing data columns in csv, Veusz rearanges my data alphabetically using the header names instead of leaving it be, meaning my column order gets messed up when I want to make an x-y plot... if you know the problem, would appreciate a short comment.

---

### Post by Neil_Hollow on 2014-06-07
Thanks for this will give it a go...

---

### Post by xadder on 2014-08-21
I discovered a nice discussion of reading text tables for python recently:

[http://penandpants.com/2012/03/09/reading-text-tables-with-python/]("http://penandpants.com/2012/03/09/reading-text-tables-with-python/")

Currently I am trying the "pandas" python package for this stuff (available in repos). For example, if the headers are  aa, bb, zz, cc and I read the data as "dat", then I can get the zz column with dat.zz. Neat.

---

