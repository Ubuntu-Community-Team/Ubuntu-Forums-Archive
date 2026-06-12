---
title: "Two unlock screens on Lubuntu 18.04 LTS?"
date: 2018-11-18
forum: Desktop Environments
---

### Post by heliosstudios on 2018-11-18
I've been using Lubuntu 18.04 (LXDE) on a laptop for a few months now and love it! Tested a variety of different packages such as KiCAD, GiMP, WINE, Opera, Audacity, Kdenlive, etc.  Recently for some reason, Lubuntu is asking *twice* to log in when the laptop lid is opened. 

A similar question already exists here: [https://askubuntu.com/questions/633484/two-lock-screens-when-unlocking-my-computer](https://askubuntu.com/questions/633484/two-lock-screens-when-unlocking-my-computer) however that says that removing 'gnome-screensaver' is the solution, which is not included with Lubuntu.  Any ideas?

---

### Post by heliosstudios on 2018-11-18
Turns out, the culprit was 'x-screensaver'.  If this is installed, *it* will present a lock screen *in addition to* the system.  So the solution is to either 'sudo apt remove xscreensaver', or modify the preferences.  If you wish to keep x-screensaver (perhaps will work for gnome-screensaver also), then go to Preferences --> Power Manager and change "Lock Screen" to "Suspend":

[IMG]https://i.stack.imgur.com/V667d.png[/IMG]

---

