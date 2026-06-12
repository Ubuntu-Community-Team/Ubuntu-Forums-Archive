---
title: "i/o error when trying to install 8.04"
date: 2008-04-24
forum: Desktop Environments
---

### Post by kickehy on 2008-04-24
Hi everyone, I'm having a real rough time trying to install 8.04...I have two different cd-rom drives (both of which are fairly new) and I get errors whenever I try to install 8.04 from either drive. The first drive, after booting up to the screen where you can choose to install ubuntu, just gives an error of "I/O Error" then all you can do is click on reboot. The second drive actually allows you to go through the install process until it actually tries to copy files. Then, of course, I get the lovely I/O Error on any random file it decides to occur on while copying files. This IS a fresh install, NOT an upgrade. Any ideas?

Thanks,
Kickehy

---

### Post by yotam on 2008-09-27
Try adding ```
all_generic_ide
``` to the boot parameters.
See also [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/259901]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259901")

---

### Post by jimmyhacker on 2008-09-27
if you had an error while burning .iso image in cd,you can get errors like this.but if you got the cd from other place,this can be brnt unsuccesfully.try to install it while windows is open from putting cd when windows is open.you can select install in windows,take 
the cd back and reboot.you an select ubuntu from windows boot menu.and you can select install ubuntu.it will install ubuntu without needing to format any drive.if it fails use alcohol 120 to burn iso image virtually.you can download iso image from

[here download]("http://download.ubuntu.com")

once you resolve situation mark solved the thread

---

