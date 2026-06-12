---
title: "Dell SP2008WFP LCD Issues"
date: 2007-10-28
forum: Dell  Ubuntu Support
---

### Post by Scubastev013 on 2007-10-28
I have a Dell SP2008WFP 20 inch monitor attached via VGA to my Dell Inspiron E1505 with a Nvidia GeForce 7300 (think)  I want to make it a secondary display, but all preset drivers and setting in the display manager result in awful resolution.  What should I do?  I've checked the Dell site for drivers and stuff.  Shouldn't Dell stuff work with Dell stuff?  Please let me know what I should do.

---

### Post by lleonard on 2007-12-12
Try:

sudo dpkg-reconfigure xserver-xorg

Then edit (sudo gedit) the xorg.conf file to make sure X is using the "nvidia" driver instead of the "nv" driver.  

Restart X and change your screen resolution to 1680 x 1050, then change font rendering to use subpixel smoothing.

---

