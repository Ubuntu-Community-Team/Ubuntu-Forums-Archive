---
title: "Unbelievable long boot"
date: 2005-12-18
forum: Desktop Environments
---

### Post by rklauco on 2005-12-18
I have two different Ubuntu installations on very similliar HW.
The first one acts as a home video/data server using freevo, samba and nfs.
The second one should be a desktop computer.

Problem is, that the desktop computer boots for more than 3 minutes. I got to the message "Loading modules" and I get stuck for 2+ minutes. Than, everything runs smooth and fast, but this loading process...

HW specification is not that bad - Sempron 2.2GHz, 1GB memory, nForce2 chipset, IBM 120GB hdd and ATI 9550 graphics.
Even Slax live distribution is loading faster than installed ubuntu.
Does anyone know where to look in logs to find out what is happening during the "Loading modules" phase?
Can anyone drop me some tip how to speed up the startup?

Is hibernation working for you? I get only HDD shutdown and the processor is still running - seems to me more than a sleep mode than hibernate.
Using hibernate I was able to start the computer in 9 secs. in XP...

---

### Post by rklauco on 2005-12-18
Later I found the probelm.
It is caused by 100GB partition on my hard drive.
No matter what filesystem is on it (tried reiser, ext3 and vfat) I still get VERY long startup time.
Removing that partition from fstab makes a miracle - I boot into system in a minute...

Any tips why is it so slow?
On the second "server" PC I have 200GB primary and 160GB secondary drive, both on ext3 and the boot time is still under a minute.

---

### Post by schdefan on 2005-12-18
You said it takes quite a while to load some modules. Can you find out which one causes the troble..
Take a look in /etc/modules or just call lsmod and post it here.
schdefan

---

