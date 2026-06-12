---
title: "3d Cube dont work"
date: 2009-05-03
forum: Desktop Environments
---

### Post by bartje545 on 2009-05-03
Hello,
[I]I have installed Linux a few days ago. I saw at va video at youtube nice effects (like the 3d cube) but I can not do that. I have searched the internet, and I find that I have to put in the terminal:
[/I]```
~$ compiz --replace
```I do that, and I get the following output:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```I press ctrl alt left mouse to get the cube.

Thank you,
Bart

---

### Post by overdrank on 2009-05-03
Hi and welcome, what is the model of the graphics card? You may use the command ```
lspci
``` in the terminal witch is located under applications, accessories. Look for VGA.
You may also look at the link in my signature on the FAQ's

---

### Post by zvacet on 2009-05-03
Go to the system>preferences>appearance>visual effects and set them to extra.Read [this]("http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/") and maybe it would be helpful to you.

---

