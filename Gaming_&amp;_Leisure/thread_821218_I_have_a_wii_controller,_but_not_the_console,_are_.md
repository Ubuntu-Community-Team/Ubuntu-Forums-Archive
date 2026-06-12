---
title: "I have a wii controller, but not the console, are there any laptop games?"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by Stochastic on 2008-06-07
I've bought a wii controller to use in sound synthesis, but I'm wondering if there are any games for my computer that I could use the controller for?  Running Ubuntu 8.04.  Thanks.

---

### Post by Sockerdrickan on 2008-06-07
A new version of my GB/C emulator will be released August 1st. It will have Wiimote support [http://youtube.com/watch?v=tCkFrF1PYJg](http://youtube.com/watch?v=tCkFrF1PYJg)

---

### Post by Rhubarb on 2008-06-07
Any game / program that can use mouse / keyboard / joystick input can use the wiimote as an input device.
So you can really use it with any game that Ubuntu can run.

---

### Post by Stochastic on 2008-06-07
Rhubarb, to what extent will the wii work with other games?  Is it just a fancy arrow keypad (no motion sensor data)?  What packages will I need?  I've gotten wmgui working, but most of the other wii packages I've been playing with are implementations of the libcwiid library for audio programming languages.

---

### Post by Rhubarb on 2008-06-08
It is possible to bind any mouse button / keyboard button / joystick button to any button (except the power button) on the wiimote.
It is possible to use the inbuilt accelerometers to control mouse movement, an IR light source near your monitor will also work for mouse input, and it is possible to use an IR LED pen to use as a mouse like a whiteboard.

CWiid allows you to get your motion sensors + IR source near monitor working.
An old tutorial to get this working is here:
[http://ubuntuforums.org/showthread.php?t=535659](http://ubuntuforums.org/showthread.php?t=535659)
Please note that this tutorial is out of date, and can be done without having to compile anything in Ubuntu Hardy.
- I'm thinking I should write up a newer *how to* for this.

To get your wii whiteboard working grab the appropriate deb file here:
[http://code.google.com/p/linux-whiteboard/](http://code.google.com/p/linux-whiteboard/)

If you get the wii classic controller it is possible to play side scrolling games like smc with it.

If you would like some help with all this, let me know and I'll write up a nice *how to* about how to get all this working.

---

### Post by Stochastic on 2008-06-09
Just one point of clarification:  If I do this, will everything in my X function normally until ```
sudo wminput -c ir_ptr
``` is executed?  Then return to normality when the wiimote drops its connection?


I really was hoping to find some games that fully utilize the motion sensing capabilities of the wii.  Do any exist (even in emulator format)?

Edit: Hmm, through some searching, this site: [http://www.wiili.org/index.php/Main_Page](http://www.wiili.org/index.php/Main_Page) Led me to this game [http://recursive.dk/wingpong/](http://recursive.dk/wingpong/) but it didn't want to run right away and I've got too many other projects to start troubleshooting this right now.

---

### Post by Rhubarb on 2008-06-09
Stochastic, there is no need to run wminput with administrative privileges.
Yes, when you disconnect your wiimote everything will run fine just as it always has.

Google Earth is a great app to use you wiimote with, so are other programs like elisa (media centre app).

If you get the whiteboard working, I recommend you try out phun:
[http://phun.cs.umu.se/wiki/Download](http://phun.cs.umu.se/wiki/Download)

And if you've got wine, and the dll file from another windows installation, you should try out Crayon Physics:
[http://www.kloonigames.com/blog/games/crayon](http://www.kloonigames.com/blog/games/crayon)

---

### Post by Wobedraggled on 2008-06-09
If you get the Wii version of the GH3 guitar, you can play frets on fire with it :0

---

### Post by Rhubarb on 2008-07-09
I've made up a tutorial to get the wiimote working as a mouse / joystick in Ubuntu 8.04
It's quite easy to follow, and does not involve compiling anything:
[**HOWTO: Wii remote in Ubuntu 8.04**]("http://ubuntuforums.org/showthread.php?p=5232024")

---

### Post by grossaffe on 2008-07-09
I've used programs like Cwiid to get my wiimotes working with linux, but i've found that they can't beat the program written for windows called Glovepie.  when i want to play games with my wiimote, I grudgingly boot into XP.  but its worth it so I can play The zelda OoT using TP controls.  many scripts are already written for that program that brings great functionality to many different games.

---

