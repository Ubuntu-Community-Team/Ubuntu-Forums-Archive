---
title: "OpenGL Problems with games."
date: 2007-02-20
forum: Gaming &amp; Leisure
---

### Post by laffys on 2007-02-20
Could someone help me with this;

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems


How can I fix this?

---

### Post by Perfect Storm on 2007-02-20
Which video card do you have?

---

### Post by laffys on 2007-02-20
NV36 [GeForce FX 5700LE]

---

### Post by Tuna-Fish on 2007-02-20
What drivers are you using for it?
(type glxinfo into terminal to find out, we only need the first ~5 lines of it though, not the whole ~50)

---

### Post by laffys on 2007-02-21
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by Perfect Storm on 2007-02-21
Have you installed the nvidia driver (looks like you havn't)?

---

### Post by Tuna-Fish on 2007-02-21
You don't have a 3D driver at all.

As you are running Nvidia I suggest you either follow the instructions at:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

or get a script like automatix2 that does it for you.

---

### Post by laffys on 2007-02-21
Ok thnx let me do that.

---

### Post by laffys on 2007-02-21
Getting some problems installing the Nvidia Drivers, had to do a backup recovery when did it. I'll try again for exact verbage.

***Tried it and no screen came up just after the kernel boot it was black for like 5 mins. Going to try  clean install and do the driver first.***

---

### Post by laffys on 2007-02-21
ok did the fresh install now it says the following;

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

---

### Post by laffys on 2007-03-06
got the card working thanx for all help

---

