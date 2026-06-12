---
title: "Automount gone wrong (and other stuff)"
date: 2005-09-28
forum: Desktop Environments
---

### Post by TmP on 2005-09-28
Hi!
I've been using Ubuntu for a month, and I must say, Great job.
After an early Slackware, I never thought I'd return to Linux.

Im running a Toshiba Tecra S1 laptop with 1,6Mhz and 256ram and 
one hdd of 40GB. And a mobility radeon 9000 with 32mb dedicated ram.

It's a dual boot with Grub loader in MBR.
I have the following partitions :
hda1 - 20Gb of windows native fat32, bootable
hda4 - 256Mb of linux swap space
hda5 - 6Gb for /root
hda6 - around 4gb for /home
hda7 - around 10Gb for a shared space, running on fat32, visible for windows as HDC

The partition numbers are a bit whacky, but its the fault of the "Recovery CD" that Toshiba supplies.

When I got tired of mounting them manually, I've updated the Fstab, following  instructions from [www.ubuntuguide.org](www.ubuntuguide.org)

/dev/hda1       /media/dyskc  vfat    iocharset=utf8,umask=000   0       0
/dev/hda7       /media/dyskd  vfat    iocharset=utf8,umask=000   0       0

The firs thing I noticet is that Ubuntu complained about utf8 beeing case sensitive. I dont think it matters all that much, but I guess it could be done better. Anybody knows how? ;-) 

Than, as I ran the Ubuntu once more, the partitions ware mounted, but didnt show in Computer tab or on the desktop - meaning they waren't automounted.

When all hope seemed lost, I found out that i could make the computer SOMETIMES detect them and place in their rightfull spot when I was running my laptop from batteries with WIFI killswitch set to ON position. 
Funny nah?

Does anybody know a solution to this problem?

And also...
Toshiba pisses me off for ignoring Linux support but whatever..
Apart form that , I hoticed that arter running one of the OS'es  I have to turn the Laptop completly off and wait for a few seconds before running the other OS. Otherwise it causes the OS to load slowly and have graphics problems in case of Ubuntu, and freeze during startup in case of Weeendows :???: 

Cheeers!:razz:

---

### Post by mlomker on 2005-09-28
> /dev/hda7       /media/dyskd  vfat    iocharset=utf8,umask=000   0       0


Change it to read:

```

/dev/hda7       /media/dyskd  vfat    defaults,umask=000  0  0

```

---

### Post by Irony on 2005-09-28
TmP your mounted fat partitions won't automatically appear on the desktop, you have to navigate to your /media/dyskd folder.
You can however access the folder perhaps by putting a link to it. I've placed my mnt folder in the Places folder by right clicking in a blank area of the desktop clicking;
[PHP]Create Launcher>Basic>Browse>mnt>Add[/PHP]
The mnt folder now appears in the Places folder on my gnome panel.

---

### Post by TmP on 2005-09-29
The funny thinng is, I can make them automount!:p 
It happens one in 20 times but it's possible.
Does anybody know how to turn it permanently on?

Thanx for the tip, I'll go try it out!
(still doesnt solve the problem of automounting the parts...)

---

### Post by TmP on 2005-10-04
Ok. Im absolutely positive its possible to automount partitions. 
Right now, I turned on my laptop from battery wirthin a hotspot.
While loading ubuntu, at the very beginning I've enabled the wireless card by a switch on the side of the laptop.
When it started (finally) - the hard drives were automounted and the hotspot was also connected.

Can anybody help me make this a rule?

---

### Post by beatato on 2006-06-09
> **Irony]TmP your mounted fat partitions won't automatically appear on the desktop, you have to navigate to your /media/dyskd folder.
You can however access the folder perhaps by putting a link to it. I've placed my mnt folder in the Places folder by right clicking in a blank area of the desktop clicking said:**
> Create Launcher>Basic>Browse>mnt>Add[/PHP]
The mnt folder now appears in the Places folder on my gnome panel.


Mmmh... I've just done that, but, before upgrading to Dapper, my mnt partitions appeared in "Places" as mounted partitions, not folders (or links to them). For me the two things work the same, but I can't figure out why it changed :-S

By the way, thanks for the tip, I've been trying to do it for almost an hour!

---

