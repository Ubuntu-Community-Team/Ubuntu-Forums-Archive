---
title: "ubuntu 12.04 desktop windowing problem"
date: 2013-05-13
forum: Desktop Environments
---

### Post by dereklai on 2013-05-13
We recently moved our desktop and inadvertently pull the plug while the machine was still shutting down. Now it boot ok and the window manager still came up ok. But the mouse somehow only moves vertically but not horizontally. We've moved another mouse that works fine from another system so we know it's not a hardware problem with the mouse.

We can login ok. But the system is not usable with the mouse only being able to move up or down along the left edge of the screen.

We were initially suspecting maybe some kind of hardware issue, maybe with the motherboard. However, we've been able to run things like virtualbox remotely from another system and logging into this system through ssh. So at this point, I'm thinking maybe it is more of a software corruption issue. I wanted to delete the windowing system and reload it. This finishes in a few seconds so I think it didn't really do it.

root@ddi8:/home/dereklai# apt-get remove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 601 not upgraded.
After this operation, 58.4 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 150381 files and directories currently installed.)
Removing ubuntu-desktop ...
root@ddi8:/home/dereklai# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 601 not upgraded.
root@ddi8:/home/dereklai# 

Is there a way to fix just the windowing system? Also, is there a way to reload the OS to the same partition? It seems like if I run ubuntu to try to repair the OS it tries to install the new system in a separate partition instead of an option to repair the existing one?

Would really appreciate any help or pointers.


Derek

---

### Post by dereklai on 2013-05-15
I forgot to include that we thought it was a software/configuration problem since we were able to boot off the ubuntu 12.04 DVD and the system works fine.

I saw some posting elsewhere and decided to delete /etc/X11/xorg.conf and re-ran nvidia-settings to create it. After that, it works fine! Problem resolved.


Derek

---

### Post by zombifier25 on 2013-05-15
Just a tip, ubuntu-desktop is merely a meta-package, a dummy package that points to other packages to install. Installing it will install all the needed packages, but removing it will simply remove the meta-package itself, leaving other parts intact.

Also, its description says that the package ensures proper upgrades, so it should not be removed.

---

