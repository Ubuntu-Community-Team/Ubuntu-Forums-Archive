---
title: "Installing Ubuntu in Virtual PC 2004"
date: 2006-03-12
forum: Desktop Environments
---

### Post by lee_connell on 2006-03-12
Does anyone have experience installing ubuntu 5.10 - 6.04 into a virtual pc 2004 session?  

When I attempt this the video display is jumbled and just distorted where it's unusable.  I read somewhere that ubuntu uses 24bit and virtual pc doesn't support that, however how do I get my installation to work, is there boot param I can add to fix this?

Thanks.

---

### Post by ajkochev on 2006-03-18
Part of the reason is alot of screens try to use 32bit color mode which is not supported in Virtual PC 2004.  After the inital CD menu loads for 5.10 set the options to use text only or a resolution with 16 bit color mode or less(sorry I can't remember the exact screens but there were options on the first CD Menu that came up).  This should get you through the installation.  After the installation the default is set to 32bit color for the login screen, so the first real boot gives you a stretched/corrupted login box.  Reboot and press Esc at the Grub loader and boot into recovery mode and run: 

sudo dpkg-reconfigure xserver-xorg

at the command line.  This will let you configure Xwindows to only use 16bit color modes.

Don't use Drake 6.04 right now, for some reason even it's command lines and recovery console are graphically corrupt in Virtual PC 2004.  Hopefully they will fix this before the finally code is released.

---

### Post by lee_connell on 2006-03-18
Thanks for the reply,

I did manage to get drake to load.  I just had to hit F4 or F3 for (VGA) on CD boot and changed the resolution there.  I was then able to finish the install with no problems. 

When I booted into the corrupted GDM, I just ALT + F2 to a new console and changed the Default 24 to Default 16 in xorg.conf and then CTL + ALT + BACKSPACE to reload GDM and everything is fine.

---

### Post by ajkochev on 2006-03-19
I cannot get the Alt+F2 to work, nothing happens when I press the keys after I load the recovery console or the regular login.  But I'm not sure what the GDM you talk about is.

---

### Post by lee_connell on 2006-03-19
Hey the GDM, (Graphical Display Manager).  Where you login.

Try CTRL + ALT + F2 that should bring you into a virtual console where you can edit the xorg.conf file.  Then exit that console or CTRL + ALT + F7 to get back to the GDM, where you login and hit CTL + ALT + BACKSPACE to restart the GDM.

---

### Post by ajkochev on 2006-03-19
That worked!  I was able to get to running.

---

### Post by lee_connell on 2006-03-19
:) glad to see you were able to do it!

---

