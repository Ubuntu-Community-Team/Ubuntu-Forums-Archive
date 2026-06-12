---
title: "beryl help would be awesome"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by b0rderline99 on 2007-08-23
so i am a complete linux newb, i just got it yesterday, and what convinced me to get it was some shots i saw of beryl.

so i have feisty installed fine, dual booted with XP, but i cant get beryl to run.

i did a beryl --replace and here is what it came up with

> ************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Xlib: extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
beryl: glXCreateContext failed
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

could someone tell me what i did wrong/need to change/etc?  any help would be awesome! :)

---

### Post by Naegling23 on 2007-08-23
two parts to this response:

1) beryl is dead.  It merged with compiz, what you want is compiz-fusion, it has all of the stuff from beryl.

2) if your new to linux, a program like automatix, or automatix bleader (which should have the 3d effects) might be the best thing to get started.  There should also be some other installation programs.  

In order for the composite engines to work, you have to add some lines to your xorg.conf file, and make sure that you have the proprietary drivers for your video card installed.  Its not a hard installation once you know your way around linux, but when I first started, it was overwhelming.  I used automatix bleader (i think) to set it up for me.

---

