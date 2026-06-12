---
title: "Beryl Help ATI 9600SE"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by Kwisniew on 2007-04-26
Been using Ubuntu for a couple of months and with 7.04 release trying to get Berly to work with ATI 9600SE. When I run the manager beryl-manager I get the following in the xterm window:

/usr/bin/compiz.real: No compsite extension
Windows manger warning: Screen 0 on display "0:0 already has a window manager; try using the -- replace option to replace the current window manager.

It goes through the Berly system compatiblity check

Detected xserver              : AIGLX
Checking for XCompostie extension           : failed

No composite extension
beryl No compsite extension
Window manager warning: Lost connection to the display '0:0';
most likely the X server was shut down or killed/destroyed the window manager.

In addition, I have yet to get compiz to work either with this card. I have checked the driver 
using the fglrxinfo command and this looks fine:

display:  0:0 screen: 0
OpenGL vendor string: ATI Technoogies INC
OpenGL renderer string: RADEON 9600SE
OpenGL version string 2.06334  (8.34.8)

Stuck, any help would be great, thanks.

---

### Post by ovidiub on 2007-04-26
Follow this guide [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL).
Good luck.

---

### Post by hyperair on 2007-04-27
Try posting your xorg.conf here. Perhaps you disabled the Composite extension by mistake

---

### Post by kpolice on 2007-04-27
> **hyperair said:**
> Try posting your xorg.conf here. Perhaps you disabled the Composite extension by mistake

It is not by mistake :P , you have to do it with the fglrx driver.

---

### Post by Kwisniew on 2007-04-27
Thanks, I ended up doing a reinstall with 7.04. I think the upgrade with my on board
graphic and the ATI got messed up. New installed worked fine, know on to getting Berly working!

---

