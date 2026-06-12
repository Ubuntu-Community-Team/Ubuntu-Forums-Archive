---
title: "xserver broken"
date: 2010-07-25
forum: Desktop Environments
---

### Post by ralphmerridew on 2010-07-25
I recently switched from Karmic to Lucid, but after doing so, my xserver stopped working.  Attempts to upgrade to Maverick fail with error

libdrm-nouveau1: breaks xserver-xorg-video-nouveau (< 1:0.0.16 but 1:0.0.15+git... is to be installed)

How can I get my xserver working again?

---

### Post by randywilharm on 2010-07-25
enter in terminal:

startx

or

enter this in the terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

this resets the xserver to default.

---

### Post by ralphmerridew on 2010-07-25
X starts up, displays a black screen with the mouse pointer, and does nothing else.

I have to use ctrl-alt-F1 to switch back to a console and ctrl-c it.

---

### Post by linux18 on 2010-07-25
Carefully:
get to a console and type
```
 xinit 
```then in the xterm terminal:
```
 metacity & 
``````
 gnome-panel & 
``````
 nm-applet & 
``````
 sudo apt-get -f 
``````
 sudo apt-get update 
``````
 sudo apt-get install ubuntu-desktop 
``````
 sudo apt-get upgrade 
``````
 sudo reboot 
```then report back

---

### Post by ralphmerridew on 2010-07-25
Trying to run gnome-panel gave the error that gnome-panel wasn't installed.
After I installed it, everything started up just fine.

---

### Post by linux18 on 2010-07-25
gnome-panel might have been the problem all along. There is a mysterious bug that stops X from loading around the time that the splash screen starts up and either causes a permanent freeze or crashes X. This is my overkill solution: just replace all startup files in the order that they start until everything works. thats what my commands were for, I'm trying to find a faster more targeted solution though.

---

