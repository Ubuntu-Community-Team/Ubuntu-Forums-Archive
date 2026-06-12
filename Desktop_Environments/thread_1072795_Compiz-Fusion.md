---
title: "Compiz-Fusion?"
date: 2009-02-17
forum: Desktop Environments
---

### Post by PFRules on 2009-02-17
**Hi guys, it's me again, Mario 'newbie' Tux.**

A simple question: **Is Compiz-Fusion included by default in my Intrepid Ibex DVD distro's installation?** Or do I have to download all the packages involved in tar.gz format from [http://packages.ubuntu.com?](http://packages.ubuntu.com?) I don't have Internet access in my PC, so I can't use Synaptic or aptitude/apt-get.

When I type [FONT="Courier New"]sudo compiz --replace[/FONT] I get:

[FONT="Courier New"]Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution ( 1024x768 ) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format[/FONT]

*[no shell from here, the terminal seems to remain freezed]*

I already installed the nVidia drivers for my GeForce 6600 AGP 8x and it's working fine (at least windows 'shake' when I move them...)

**Thanx in advance!**

---

### Post by oldos2er on 2009-02-17
Compiz-fusion is installed by default, look in System, Preferences, Appearance, Visual Effects. Unfortunately, compizconfig-settings-manager is not installed; it's a package that gives you a much greater degree of control over compiz. Look into AptonCD or [http://keryx.betaserver.org/](http://keryx.betaserver.org/) to install it.

---

### Post by zeealpal on 2009-02-17
either open a terminal and type 'sudo apt-get instal ccsm'
or go to synaptic, type in compiz and select advcanced desktop effect settings

---

### Post by Ng Oon-Ee on 2009-02-17
> **zeealpal said:**
> either open a terminal and type 'sudo apt-get instal ccsm'
or go to synaptic, type in compiz and select advcanced desktop effect settings
I believe you missed the fact that he doesn't have an internet connection on the PC in question.

And yes, to the OP, you need compizconfig-settings-manager installed. I'm not sure if its on the DVD, I doubt it.

---

