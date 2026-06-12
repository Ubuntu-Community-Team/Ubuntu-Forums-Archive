---
title: "Any Electrical Circuit Simulation Soft for Ubuntu???"
date: 2006-12-20
forum: Education &amp; Science
---

### Post by Slater on 2006-12-20
I use Windows since i was 7 (i'm 23 now) and all my software is in Win... 
Last week i installed Ubuntu Edgy  cause i like the ideas that it represnts
but i'm in for a treat :confused:  because i know nothing of Linux and its programmes!!!!

I use Mapple 10, Electronic Workbench(Multisim) 9, Matlab, Autocad 

If anyone knows any similar alternative program i would be REALLY 
GRATEFULL :-D :-D

---

### Post by daller on 2006-12-20
qCAD should get around your AutoCAD needs...

For Electronic simulations, I have no idea!

geda-utils (and pcb) should get around Electronic CAD, but for the simulation part, I'm also lost!

---

### Post by scrooge_74 on 2006-12-20
> **Slater said:**
> I use Windows since i was 7 (i'm 23 now) and all my software is in Win... 
Last week i installed Ubuntu Edgy  cause i like the ideas that it represnts
but i'm in for a treat :confused:  because i know nothing of Linux and its programmes!!!!

I use Mapple 10, Electronic Workbench(Multisim) 9, Matlab, Autocad 

If anyone knows any similar alternative program i would be REALLY 
GRATEFULL :-D :-D

Check the repositories, is not my thing, but I think I saw some program about electrical circuits, sorry don't remember the name. Should be easy to check in synaptic.

There is a section call electronics and I see a program for designing printed circuits.

Also in the Science (universe) section 

I use to have an Atari and use DOS 3.0 when I was a kid :D

Now I am older and use Ubuntu LOL

---

### Post by newsman on 2006-12-20
according to what i have read on ubuntuforums...scilab and octave came us recommended matlab alternatives... if you do manage to setup matlab on ubuntu,,,make note of how you did in the community docs ;) if ur version of matlab is fairly old though aparently it was installable after much hackery and hong kong foey stuff, as for workbench alternative,,, i don't really know as an electronic student, i need to get my head around that too... however i am busy trying to use software for communication simulation, (omnetpp, ns-2 kind of stuff, and linux has much more tools than windows for this type of stuff rather than simulation of circuits.)

---

### Post by fifafrazer on 2006-12-20
Ktechlab is pretty nice for Circuit simulation. It's still in a early stage, so it has some bugs, but it's worth looking at.. The only bug i have, is that the incurcuit simulation of PICs are missing..

Otherwise there is Qucs - Quite universal circuit simulation.. But ktechlab is nicer ;)

---

### Post by daller on 2006-12-21
> **fifafrazer said:**
> Ktechlab is pretty nice for Circuit simulation. It's still in a early stage, so it has some bugs, but it's worth looking at.. The only bug i have, is that the incurcuit simulation of PICs are missing..

Otherwise there is Qucs - Quite universal circuit simulation.. But ktechlab is nicer ;)

Those are nice, but not in the repo :(

---

### Post by fifafrazer on 2006-12-21
ktehclab is in the edgy universe repo.. Dont remember if Qucs can be found anywhere..

---

### Post by villindesign on 2006-12-24
LTSpice is great. There is not a *nix version, but the author ensures that is always runs on wine...

I use if for all my circuit simulations.

---

### Post by villindesign on 2006-12-24
It is easy to install. Here are the steps:
[LIST=1]
[*]download program from [Linear Technology]("http://ltspice.linear.com/software/swcadiii.exe")
[*]open terminal
[*]-$ wine swcadiii.exe 
[*]press accept & install now
[*]the installer will put a icon on your desktop and launch the program
[*] if you delete the program icon, you can always type $wine "C:\Program Files\LTC\SwCADIII\scad3.exe" in the terminal
[/LIST]

Have fun!

---

### Post by boz on 2006-12-27
> **Slater said:**
> I use Windows since i was 7 (i'm 23 now) and all my software is in Win... 
Last week i installed Ubuntu Edgy  cause i like the ideas that it represnts
but i'm in for a treat :confused:  because i know nothing of Linux and its programmes!!!!

I use Mapple 10, Electronic Workbench(Multisim) 9, Matlab, Autocad 

If anyone knows any similar alternative program i would be REALLY 
GRATEFULL :-D :-D

You can get a Linux version of Maple 10.  I think that if you already own a license for Windows, they'll even give you a discount, but I'm not absolutely sure.  Alternatively, you can try Maxima with WxMaxima.  Both are in the repositories, though last time I tried it, that program seemed to be broken . . . 

For a circuit simulator, you can try gEDA, which is in the repositories.  I prefer downloading the source code and installing it manually, but that might be over your head right now.  You should probably try LTSpice as villindesign suggested.

For a Matlab replacement, I use Octave, but you also have to install it from source.  Scilab is in the repositories, so it will be easier for you to install.  The catch is, Scilab uses its own syntax and commands whereas Octave is almost a perfect clone of Matlab.  I've seen someone on this forum mention that there is a program out there to translate Scilab code to Matlab code, but I think not back?  Do some digging on this Education & Science forum for more on that.

I've never had any use for Autocad, so someone else will have to help you with that one.  Good luck!

---

### Post by jhaitas on 2006-12-27
check out spice... it is quite standard

---

### Post by shaihulud on 2007-04-16
MATLAB has a unix/linux installer also I would use SwCADIII from LT its one of the better ones out ther and it's free.

---

### Post by hsweet on 2007-04-17
I've used Microcap and MMLOGIC running Wine.  Microcap has a good free version so long as you don't need large component counts and mmlogic is free.
[http://www.spectrum-soft.com/demoform.shtm](http://www.spectrum-soft.com/demoform.shtm)
[http://www.softronix.com/logic.html](http://www.softronix.com/logic.html)

Cad might be harder.  good luck

---

### Post by itchy8me on 2007-09-12
QUCS is deinitely a very promising circuit simulator! i also use sci-lab, for 3d cad yoiu can try the commercial version of arcad.. mm.. there was another one, cannot remeber its name.

aahh yes vrlcad or something to the likes, salome is also pretty cool, although its pretty hard to install. another good free one is brlcad, this one is however command line based, but it is very powerfull.

---

### Post by hsweet on 2007-09-15
You can check out wxmaxima (in the repository) for maple.  Native linux, so no wine problems

---

### Post by bubbalouie on 2007-09-16
Villindesign is right, LT's swcadiii is beautiful under wine, I use it personally and have never had any problems.

Sadly I can not say the same of Protel :(

Matlab has a linux installer, as for Maple I never really used it outside of uni (as required and even then grudgingly).

---

### Post by already710 on 2009-05-30
Thanks for the comment bigbird. I couldn’t agree more. A little helpful information never hurt anybody! :KS
[[color=#FFFFFF]_simulation credit_[/color]](http://simulationcredit1.com)

---

### Post by tryinghard on 2010-01-02
Hi have you tried WINE? TO RUN WINDOWS PROGRAMES ON UBUNTU? i USE IT TO RUN THE STARCRAFT DEMO FOR WINDOWS. TRY IT ITS OPEN SOURCE.

---

### Post by hsweet on 2010-01-02
Navive linux apps

Qucs, Ktechlab are both decent electronics sims.   mmlogic is good too, but needs wine

qcad is decent for 2d cad

Check out graphiteone for 3d cad.  not open source, but very similar to pro engineer, free for personal use.

---

### Post by arvevans on 2010-01-02
Here is a list to check out:
[INDENT]
[LIST]
[*]Electric (Electrical CAD system)
[*]Qucs  (Circuit Simulator)
[*]tkgate (Digital Circuit Simulator)
[*]Eagle Cad (Electronics CAD)
[*]gEda  (a full featured EDA system for Electronics design)
[*]Oregano (another kind of Spice)
[*]Gsmc (Smith Chart Generator)
[*]GTK  (Smith Chart Calculator)
[*]Qqntenna (NEC File Viewing Tool)
[*]xcircuit (Circuit drawer with Netlist & Spice outputs)
[*]xnec2c (Viewer for NEC2)
[*]Gerbv (Gerber File viewer)
[*]Kicad (Electronics CAD & PCB)
[*]gwave (Waveform viewer)
[*]baudline (Spectrum Analuzer)
[*]ExpressPCB (free software runs with WINE)
[*]PCB123 (Porprietary Scematic & PCB CAD, runs with WINE)
[*]Elsie (Filter Design Tool)
[*]BodeCad (schematic editor circuit analyzer, runs with WINE)
[*]Sunstone PCB123 (Design Suite runs with WINE)
[*]AppCAD (Agilent Technologies AppCAD, runs with WINE)
[/LIST]
[/INDENT]
Those are just a few of what is available, and some of what I have installed and use.  There are many more such tools.  Almost all the UNIX electronics tools for electrical engineering have been ported to Linux and can be found and installed with a little searching.

Go to the Ubuntu software libraries and search for "CAD", "Electrical", "Simulation", and Ham Radio" as individual searches.  You will find a rich list of things to play with.

Then go to the Debian repository and do similar searches to find what might have been missing from the Debian archives.

If you find .rpm software that you want to try, you can usually use the "alien" installer to convert these to .deb installable files for Ubuntu.

Arv
_._

---

