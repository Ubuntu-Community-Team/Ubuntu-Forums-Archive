---
title: "Terrible OpenGL speeds VS Windows"
date: 2005-07-08
forum: Desktop Environments
---

### Post by Quest-Master on 2005-07-08
I ran a few simple OpenGL tests the other day and..

I run it on Ubuntu, and get around 25FPS. And on Windows? 225.

I am using the vesa driver and am on an Intel Integrated Graphics Extreme Card. Anyone know how to up it near Windows's FPS or faster?

---

### Post by hal8000 on 2005-07-09
What tests did you do?   Running tuxracer with the frames options display under both linux and  windows may give you a better idea of permorance.

---

### Post by endy on 2005-07-09
I don't think you want the VESA driver in your xorg file for openGL acceleration, I'm not sure what you need for an intel chipset (I've never had one) but maybe you need the "i810" driver.

---

### Post by JLTB on 2005-07-09
Hi Quest-Master,

The VESA driver is not a hardware accelerated driver.  It uses your CPU to render graphics (slow).  Depending on what chipset your graphics card is you will need to install the correct drivers (ATI, NVIDIA, S3 .. etc).  Once you get those going you should get "comprable" performance.  Keep in mind that unless you are benchmarking with the same benchmark program on both systems your numbers may be misleading (I get 4000fps in glxgears, but of course I don't get 4000 fps playing HL2 in windows).

good luck.

---

### Post by Quest-Master on 2005-07-09
I want to use i810, but I was having problems earlier as it wouldn't go above 640x480, even after a dpkg-reconfigure xserver-xorg and i810switch. Oh well, I guess I'll try again though  :\

---

### Post by Quest-Master on 2005-07-09
Update: sudo dpkg-reconfigure xserver-xorg ends with a black screen, and changing the driver in xorg.conf to i810 changes to a 640x480 resolution and the Screen Resolution tool only lists that resolution as available under.

---

### Post by charlieg on 2005-07-23
[QUOTE=Quest-Master]Update: sudo dpkg-reconfigure xserver-xorg ends with a black screen, and changing the driver in xorg.conf to i810 changes to a 640x480 resolution and the Screen Resolution tool only lists that resolution as available under.[/QUOTE]
 Have you tried manually edit the xorg.conf file to add the resolution you desire?  It's not too difficult and possibly worth a try.  I use the i810 driver and use a resolution greater than 640x480 without issue, although admittedly it was all picked up automatically for me.

---

