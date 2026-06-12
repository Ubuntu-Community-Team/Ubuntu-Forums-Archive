---
title: "Artifacts appearing"
date: 2010-11-20
forum: Desktop Environments
---

### Post by SuperFreak on 2010-11-20
I am periodically getting artifacts appearing on my screen on my desktop screen (see attached image bottom right next to calendar).The artifacts stay on top of the screen if I open Firefox, Thunderbird, Open Office etc. I have tried uninstalling 3D-accelerated proprietary graphics driver for NVIDIA cards, Cairo Dock and selectively uninstalling Screenlets with no change. I have 64 bit Meerkat installed on a AMD X2 4200+ machine with a Nvidia 7600GT graphics card.
I am wondering if the graphics card might be the source of the problem.

---

### Post by jmet on 2010-11-20
I get the same thing from clicking on the Gnome menus when opening an application, I have an ATI video card and am running the proprietary drivers.

A ghost menu display that overlaps open application windows and will go away after a long while.

---

### Post by SuperFreak on 2010-11-24
Is there a solution for this?

---

### Post by jelabarre on 2010-11-30
This is not just a 64bit problem.  I am running Ubuntu 10.10, 32bit, compiz completely removed, Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller for video, standard Gnome desktop.  If I happen to remember what menu or popup had created the object in that place, I can clear it by re-opening that item.  Otherwise it's there until I log out.

---

### Post by grahammechanical on 2010-11-30
When you boot do you see a motherboard splash screen? If so, do you see any changes (artifacts) on that image?

This happened to me. It also showed up as yellow lines over the white of the Grub boot menu. and as blue lines or yellow lines over white areas on the screen.

The graphics card was overheating (silent type. No fan). Eventually Ubuntu would only boot in low graphics mode. Then not boot at all. The boot process would drop into a command line terminal. The BIOS in the graphics card had became corrupted and the boot process could not determine the settings for the monitor. It knew I had a screen but could not find a configuration file. In the end I could not even run a live CD to reinstall. New card fixed all that.

It might be bad news. Sorry.

Regards.

---

### Post by SuperFreak on 2010-12-01
It may be a problem with the graphics card; it is typically running at 54-57 C which puts it into the red zone on the Gnome Sensors applet but according to searches on Google is in normal range. I am not seeing the artifacts on the Splash screen though. The Nvidia card I use does have a fan.

---

### Post by jelabarre on 2010-12-01
Well, seeing as it happens on 2 different laptops (the T61 with the Intel video, and a T42p with ATI FireGL Mobility T2).  No problems in the BIOS logo, and the artifacts go away if you log out.  However, that's quite a drastic solution, which would require me to close down terminal windows where processes are running, and sometimes that opportunity doesn't present itself for a while.


This is with *32-bit* Ubuntu, not even 64-bit which is being reported here.  So the problem is more pervasive.

---

### Post by openprivacy on 2011-09-19
I am also seeing artifacts from menus.  64-bit Ubuntu 10.10, VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series])

This didn't happen in 9.4 but first showed up in 10.4 and upgrade to 10.10 didn't help.  I have seen the problem both with and without the ATI proprietary FGLRX driver.

Logging out and back in removes the aritfacts, but as another poster mentioned, that is not always optimal as it requires closing all open sessions.

Any solution to this?  Do you think an upgrade to 11.4 will solve it?

---

