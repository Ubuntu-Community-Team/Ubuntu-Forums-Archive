---
title: "translucid windows"
date: 2008-02-22
forum: Desktop Environments
---

### Post by shadow_yada on 2008-02-22
Hi I am looking forward to get my windows transparent on my Ubuntu distribution 
I am running Ubuntu 7.10 and this are the Specs of my system
Dual Core processor Pentium D 
1GB of memory Ram 
Nvidia 6700
Any type of help I would appreciate it   :KS

---

### Post by Yes on 2008-02-22
Compiz fusion can do that.

First, install CCSM: sudo apt-get install compizconfig-settings-manager.  Then go to System -> Preferences -> Appearences, and go to the Effects tab.  Select "Custom" and close the window.  Then go to system -> Preferences -> Advanced Desktop Effects Settings, General Settings, Opacity Settings.  Click on add and enter the window type and the opacity setting.  So if you want the terminal to be transparent, for the window type put "name=gnome-terminal".  See [here](http://wiki.compiz-fusion.org/WindowMatching) for how to identify window names, classes, etc.

---

