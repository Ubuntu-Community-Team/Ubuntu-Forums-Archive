---
title: "Looking for 64bit..."
date: 2008-08-30
forum: Education &amp; Science
---

### Post by ms277017 on 2008-08-30
I see that Maple sells a 64bit linux version... Are there other "maple like" programs that are (64bit) (must be 64bit).  That have a maple feel?  I really want to use MAXIMA, but its 32bit, unless someone knows about a 64bit version?

All in all I want a "gnu" like maxima that has the feel of maple (like maxima) that is (64bit).

I am a math major, not much scientific use, just pure math mainly.

---

### Post by forger on 2008-08-30
Not sure if any of these help, but I found:
scilab
> Matrix-based scientific software package (a la Matlab and Xmath) 
Scilab is a matrix-based scientific software package resembling Matlab and Xmath. Scilab contains hundreds of built-in mathematical functions, rich data structures (including polynomials, rationals,linear systems, lists, etc...) and comes with a number of specific toolboxes for control, signal processing, ...
This package contains the architecture independent files.

Also found these:
> axiom - A general purpose computer algebra system: main binary and modules
mathomatic - Portable Computer Algebra System (CAS)
kalgebra - calculator based on MathML language
jacal - Interactive symbolic math system
maxima - A computer algebra system -- base system
kayali
wxmaxima
magnus

---

### Post by ms277017 on 2008-08-30
Thanks for the reply. is that a 64bit maxima? all the ones I have found are 32bit.  I like matlab too and maple. Matlab isnt 64bit for linux yet though.  I do not mind paying...  Ill probably just buy maple for linux since it is 64bit.

---

### Post by forger on 2008-08-30
> **ms277017 said:**
>  is that a 64bit maxima? all the ones I have found are 32bit.  I like matlab too and maple.

I'm sorry, I wasn't clear: All the above I listed are **package names** :)
Hence you can use a command in Applications > Accessories > Terminal, such as:
```
sudo apt-get install **packagenamehere**
```
..where packagenamehere should be substituted with one of the programs above

Yes, there is a 64-bit version of maxima: [http://packages.ubuntu.com/maxima](http://packages.ubuntu.com/maxima)
Click on "**amd64**" to download the deb package and double click to install, or you could just follow the above and execute
```
sudo apt-get install maxima
```

---

### Post by ms277017 on 2008-08-30
octave looks good but I cannot figure out if its 64bit or if it is which official file to download.

sorry I do not have my computer yet and I am not sure if I can pratice installing stuff off the live cd...
Juts want to be ready when my computer arrives.

---

### Post by gmxgeek on 2008-08-30
Number one rule of ubuntu:
ALWAYS try the repository first unless you have a really good reason not to.
Execute this in terminal
```

sudo apt-get install maxima

```

and you should be all set to go. It will select the one that is right for your system if it exists, and if it doesn't, then it will tell you so

---

### Post by ms277017 on 2008-08-30
nice I have never seen that search feature... thanks man.


I am a linux noob guys sorry... still trying to learn how this stuff works.  how do you access the reprository?

---

### Post by gmxgeek on 2008-08-30
There are two ways. One is from command line such as in the previous post, and the other is through a GUI called Synaptic. To launch synaptic, go to System->Administration->Synaptic

This might help
[http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

---

### Post by ms277017 on 2008-08-30
I installed all of maxima and octive yet cant get either to run **I am a total windows noob**  how do I execute? or make the program start?  
Im running the live version of HH 8.04 cause my windows computer died and my new ones not here yet, but I still need to know how to do this type of stuff for when I get my new linux comp.

---

### Post by rybu on 2008-08-30
Although Maple *says* their software is 64-bit, it's not entirely true.  If you are running only the 64-bit kernel, you can't install Maple.  

Their install software is 32-bit only.   I'm not sure if there's anything substantially "64 bit" about Maple.  Basically, you can run it on a 64-bit system provided you have all the 32-bit compatibility libraries installed. But you can't otherwise. 

Kind of sad.

---

### Post by Sef on 2008-08-30
> I installed all of maxima and octive yet cant get either to run **I am a total windows noob** how do I execute? or make the program start?
Im running the live version of HH 8.04 cause my windows computer died and my new ones not here yet, but I still need to know how to do this type of stuff for when I get my new linux comp.

Check their website for directions or help or both:

[Maxima]("http://maxima.sourceforge.net/") website.

[Octive]("http://www.gnu.org/software/octave/") website.

---

### Post by ms277017 on 2008-08-31
> **ms277017 said:**
> I installed all of maxima and octive yet cant get either to run **I am a total windows noob**  how do I execute? or make the program start?  
Im running the live version of HH 8.04 cause my windows computer died and my new ones not here yet, but I still need to know how to do this type of stuff for when I get my new linux comp.


Any ideas on this  ^^^

didnt see the 2nd page nm :) thanks for the info.

---

### Post by ms277017 on 2008-08-31
does anyone use maxima and know how to launch it after install? 
web page does not address such linux noob questions such as this one

---

### Post by kjohansen on 2008-09-02
to run maxima open a terminal and type maxima.  to run octave type octave in a terminal.

to open a terminal go to Applications->accesories->terminal.

you can also make an application launcher on the desktop by right clicking->create launcher.  Change type to application in terminal, and type maxima in the command box.

Maxima also has a gui you can get it by doing:

sudo apt-get install wxmaxima

Octave has several GUIs I use Qtoctave which you can get by doing:

sudo apt-get install qtoctave

---

