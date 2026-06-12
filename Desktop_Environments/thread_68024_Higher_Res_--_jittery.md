---
title: "Higher Res -- jittery?"
date: 2005-09-21
forum: Desktop Environments
---

### Post by qalimas on 2005-09-21
I have always had this problem with Linux, so I've been sticking with 1280x1024, but with a 21" monitor, it's a waste.  Now, in Windows it shamefully shows right, but in Linux, 1600x1200 is jittery :(  I have an nVidia geForce fx 5200, and the official drivers installed, running it on a 60 refresh rate.  Any ideas?

---

### Post by dbott67 on 2005-09-21
[QUOTE=qalimas]I have always had this problem with Linux, so I've been sticking with 1280x1024, but with a 21" monitor, it's a waste.  Now, in Windows it shamefully shows right, but in Linux, 1600x1200 is jittery :(  I have an nVidia geForce fx 5200, and the official drivers installed, running it on a 60 refresh rate.  Any ideas?[/QUOTE]

Can you change the refresh rate at any resolution in Linux?  What's the refresh rate set to when you set the res to 1280 x 1024?

What happens when you try to change the refresh rate when the res is 1600 x 1200 --- does it give you choices, or is 60 Hz the only option?

-Dave

---

### Post by qalimas on 2005-09-21
It's always on 60, for every res, no option to change

---

### Post by frodon on 2005-09-22
**Qualimas** you just need to add hsync and vertsync parameters in xorg.conf file, it's a well known issue of hoary, maybe it will be solve with breezy.
Therefore open your xorg.conf : ```
sudo gedit /etc/X11/xorg.conf
```and add these 2 lines in the monitor section : ```
Section "Monitor"
Identifier "Dell"
Option "DPMS"
[COLOR=Red]**HorizSync 30-76**
**VertRefresh 50-85**[/COLOR]
EndSection
```The HorizSync and the VertRefresh parameters are defined in your screen specification (you can find it on internet) and it's really important to put here the exact values coming from your screen specification. Wrong values could distroy your screen.

Enjoy  ;-)

---

