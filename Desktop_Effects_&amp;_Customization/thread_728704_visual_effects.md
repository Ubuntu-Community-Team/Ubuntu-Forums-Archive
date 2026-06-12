---
title: "visual effects"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by golfspilleren on 2008-03-19
Hi!

Some time ago it *was* possible for me to use the extra visual effects on my computer. But now it just says: "Desktop effects could not be enabled". What do I do?

---

### Post by aashay on 2008-03-19
run ```
 compiz --replace
``` in the terminal and paste the response here.

---

### Post by golfspilleren on 2008-03-19
Here it is :)

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting emerald
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by aashay on 2008-03-19
What graphics card are you using? Are you sure the drivers are correctly installed?

---

### Post by golfspilleren on 2008-03-19
> **aashay said:**
> What graphics card are you using? Are you sure the drivers are correctly installed?

I'm not sure what kind of graphic card it is. I have tried to google it, and maybe it is "Intel Extreme Graphics 2"? I don't know anything about this.. 

But my computer is an IBM Lenovo ThinkCentre M50 8189, so I don't think the graphic card is good. But as I wrote in the beginning: It has been working before, so I don't understand why it doesn't work anymore.,

---

### Post by aashay on 2008-03-19
I'm not too sure whether this will solve the problem, but try installing libgl1-mesa-glx and libgl1-mesa-dri from the repositories if they arent already installed

---

### Post by mattk132 on 2008-03-19
I think that the graphics card is onboard the motherboard.  Are you using a laptop or desktop?

---

### Post by mk1w86 on 2008-03-19
Make sure the restricted drivers are still in use.

System >> Administration >> Restricted Drivers Manager

---

### Post by mattk132 on 2008-03-19
Also, go to synaptic and search for xserver-xgl.  If it is not installed it must be!:)

---

