---
title: "xps m1330 and the nvidia geforce 8400M gs"
date: 2008-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maraja on 2008-10-23
Hi,

I am opening this thread trying to give some clue to all the xps 1330 users facing a problem with their hardware (as me).

I got my brand new xps last march (2008). Started with Ubuntu 7.10 and then upgraded to 8.04: everything was 101% fine until last week.

Then I started having troubles: every now and then, after some hours of use, the system used to crash to a black screen.

After having installed the latest bios (A12) the only improvement was that, rather than crashing, the xps rebooted...

I then decided to use the Dell Diagnostic DVD to check the system and found out that there was a problem with the hard disk having a bad sector.

Contacted Dell support and got the disk replaced in two days at no cost.

Unfortunately, even with the new disk, the problem appeared again and again... sometimes it is not even possible to boot.

I did some researches and found out that there is an issue with the Nvidia 8400 (and not only on Dell systems!) sometimes getting too hot.
There is actually a [solution]("http://forum.notebookreview.com/showthread.php?t=268081") but, unfortunately, you loose your warranty if you apply it...

Before starting considering to apply the modification, I decided to upgrade the Nvidia driver (now 177.80) and the Adobe Flash plugin (now 10.0 r12) as a friend reported there may be an overload on the system when playing flash media.

Installed Gkrellm (sudo apt-get install gkrellm) and configured it to show both the CPU and GPU (nvidia) temperatures.

Everything was fine for the entire day (yesterday) but this morning I was not able even to boot. The systems hangs to a black screen just before the login screen.

Decided to switch back to the non accelerated driver by editing the X configuration as follow (after having booted from a Live USB pen):

```
sudo nano /media/disk/etc/X11/xorg.conf
```

commented the accelerated driver (nvidia) and added a line to use the non accelerated (nv) as follow:

```

Section "Device"
     Identifier     "nVidia Corporation G80 [GeForce 8400M GS]"

#Driver         "nvidia"
Driver "nv"

    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
EndSection

```

rebooted from the hard disk: the system is now working again (no acceleration nor compiz of course).

Called the Dell support again explaining the whole story. They are aware and it looks like the motherboards produced between December 2007 and May 2008 have this issue.

Tomorrow I will have a technician here replacing the motherboard.

Will keep you updated if the new board will definitely solve the problem.

Hope it help

---

### Post by superm1 on 2008-10-23
Yeah you should be having an extension to your warranty (if it's already expired) for covering this mishap with the motherboards.  Nothing that's your fault here for being the cause, make sure you are on the latest BIOS with the new one to decrease the liklihood of the new one going bad again.

---

### Post by maraja on 2008-10-23
yep superm1,

if the new motherb fixes the problem I am going to extend my warranty that, luckily, is still alive :)

---

### Post by superm1 on 2008-10-23
What I was meaning is that I had thought Dell was providing extensions for all customers for this particular issue.

---

### Post by maraja on 2008-10-23
I see... will check with them as I live in Italy and here they do not even ditribute the Ubuntu preinstalled version.

thank you

---

