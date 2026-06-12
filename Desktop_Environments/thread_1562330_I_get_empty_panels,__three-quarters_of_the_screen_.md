---
title: "I get empty panels,  three-quarters of the screen width"
date: 2010-08-27
forum: Desktop Environments
---

### Post by ub-pir on 2010-08-27
I have just updated to Lucid but after the upgrade the Gnome Panels display as empty (no menus, apps, etc.) and extend from the LHS of the screen to around three-quarters of the screen. This happen for both top and bottom panels.

If I right click on the panels, select "Properties" and toggle the "Expand" checkbox (initially on), the panels revert to what they should be. No further problems until I log off. When I log back in again, the panels are back to blank/three-quarter width.

I am guessing  some Gnome/X11 config file is either corrupted or incompatible. (Odd because I have upgraded another machine without any problem.) Anybody any ideas?

Peter

---

### Post by BrockStrongo on 2010-08-27
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Give this a try and see if it makes your panels act correctly.
Let me know

---

### Post by ub-pir on 2010-08-27
I have tried both forms of gconf-2 (shutdown and --recursive-unset). Everything appears OK in the session but after log off and login again, the top panel now has the menus and two of the apps at the LHS. But both panels are still 3/4 width. The top panel has none of the RHS items visible. The bottom panel is still empty.

Peter

---

### Post by BrockStrongo on 2010-08-29
What kind of video card do you have?

It seems like the config for gnome-panel got botched during your upgraded, you might want to try reinstalling the gnome panel.

I also found this program [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/) it is a script to restore the panel defaults, but, it also has an option to save the panel as it is. Maybe restoring the panel and getting it the way you like, then saving the panel, will force a proper config file to be made. I don't know, but, its worth a try.

It appears as though you are not the only one with panel issues after an upgrade. 

Sorry I can't be of more help

---

### Post by BrockStrongo on 2010-08-29
[http://ubuntuforums.org/showthread.php?t=1467466](http://ubuntuforums.org/showthread.php?t=1467466)
 these people seem to be having the same problem

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550)

it looks as though there is a bug filed.

There are some workarounds listed on the bugs page

---

### Post by ub-pir on 2010-08-29
Thanks for the reply but I am beginning to suspect there are more profound problems with Lucid. Printing had stopped working as well as a few other odd things.

I tried a fresh install of Lucid but only got as far as the page where you specify partitions - the page was just blank as the installer does not see the HDD at all! 

Thinking about this, I have had mixed success with Lucid. Upgrading my PC at work was fine. A fresh install on my kids' laptops was fine. But the current PC has been a problem, as has trying to upgrade from Karmic on an old laptop. A work colleague has also been unable to install Lucid. The linking factor seems to be the age of the hardware: Lucid seems to install like a dream on newish h/w but gives a range of strange problems on old h/w. This is anecdotal, I know, but I am wondering if the changes to Lucid have removed support for older h/w as a side-effect? It would be interesting if people reporting strange  problems with Lucid could state the age of their h/w.

I have now reinstalled karmic from scratch and all is  working fine... apart from the time wasted on reinstalling everything...

---

### Post by BrockStrongo on 2010-08-29
You could be right. It seems like a large amount of install/upgrade issues are based around older h/w. Too bad though, this could be the kind of thing that puts people off ubuntu altogether, especially when support for the older releases expires. Enjoy Karmic, I know I did

---

