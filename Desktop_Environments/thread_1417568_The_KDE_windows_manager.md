---
title: "The KDE windows manager"
date: 2010-02-27
forum: Desktop Environments
---

### Post by robertsaron on 2010-02-27
I was moving my computer so rebooted it. Once it rebooted the screen resolution was 800x600. After checking the 3d drivers, they had some how become uninstalled after the reboot. Installed the 3d drivers for my Nvidia card, then rebooted. 

Desktop resolution was now back to 1280x1024. No desktop effects, this is odd since they were working before the first reboot. Then enabled/disabled some clicked apply. This is the message that came up. 

**The KDE windows manager** The following effects could not be activated: [it then lists the effects like 3d cube, log in, magic lamp etc...]

Below are my system specs, I am NOT running the KDE 4.4 beta, running latest stable release of Kubuntu.

Nvidia 6800 FX
AMD athlon XP 64
MSI motherboard with dual lan and on board audio. USB keyboard and mouse
3 gigs of RAM

I can upgrade to the beta if that would help, but last time I did everything got messed up and had to reinstall from scratch. This should work as is.

---

### Post by robertsaron on 2010-02-27
So out of curiosity I upgraded to 4.4 beta Kubuntu. Going into the desktop manager, then advanced, I changed it from OpenGL, to Xrender. 

Now when attempting to change it back to OpenGL, I get this message: 

**Sorry System Settings** Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options especially changing the compositing type.

That is the end of the error message. I also get a message now and then about how the compositing type is in use by another system. So there seems to be a problem with OpenGL, and a software conflict with the compositing type. 

Anyone know how to resolve, or what to look for in logs, and how to extract need information from logs?

---

### Post by JakeOfOz on 2010-03-31
when you go to system settings>Desktop, does it say 'compositing is disabled' ? then the effects won't work. you can press alt-shift-f11 (if I'm correct) to restore it. If it doesn't work at startup, go to the advanced tab and select 'disable functionality checks'.

good luck

---

