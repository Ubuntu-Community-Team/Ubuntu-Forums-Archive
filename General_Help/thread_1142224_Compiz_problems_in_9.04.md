---
title: "Compiz problems in 9.04"
date: 2009-04-29
forum: General Help
---

### Post by mat10000 on 2009-04-29
I upgraded to  9.04 and the performance wasn't very good and I had problems with compiz, so i tried this fix.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

I think the general performance is back to normal, but compiz still doesn't work.  Most of the time compiz isn't turned on at startup and when i try starting it up the windows boarders go away compiz works but changing anything in CCSM causes compiz to crash.

OR 

I get this error message.  (this seems to happen everytime now)

mat@mat-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault


My video card is Intel 945gm/940gml
Thanks

---

### Post by mat10000 on 2009-05-01
anyone?

---

### Post by inkrypted on 2009-05-01
Just an observation but I have noticed that 3D effects do not work very well with Intel onboard video. If this is a desktop consider getting an Nvidia card if this is a notebook consider not using compiz.

---

### Post by mat10000 on 2009-05-02
> **inkrypted said:**
> Just an observation but I have noticed that 3D effects do not work very well with Intel onboard video. If this is a desktop consider getting an Nvidia card if this is a notebook consider not using compiz.

Before I upgraded everything was working fine, and I mostly just use the simple plugins.

---

### Post by dddw on 2009-05-18
The special effects like ´wobbly windows´ work fine for me. 
The ´cube´'doesn´t however.
Most anoying thing is: that all my other workspaces don´t work either.

---

