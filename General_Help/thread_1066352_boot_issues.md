---
title: "boot issues"
date: 2009-02-10
forum: General Help
---

### Post by austin.mathews on 2009-02-10
Some help pointing me in the right direction would be appreciated.

I installed ubuntu 8.10 the other day to an external hard drive, creating a separate partition on said drive to do so. I have XP installed on my main internal drive. Now, when I boot up my PC with the external turned on, I'm naturally taken to the GRUB loader to select my OS. However, when the external is unplugged upon boot I simply get Error 21 from GRUB.

Furthering my problems, XP does not recognize the partition where Ubuntu is installed. I can't find it, anywhere.

I am no means expert, so is there a way to remedy this? Say, get XP to boot when my external is not plugged in and get XP to recognize the partition?

Sorry, I think I may have gotten in a little over my head, but a point in the right direction would be appreciated.

---

### Post by louieb on 2009-02-10
Grub  uses two programs stage1 which by default gets installed in the MBR of the 1st drive in the boot order.  and stage2 which can be found in /boot/grub.  If your computer supports booting to your external drive it can be fixed this way. 

use your windows install CD boot to the recovery console and run **fixmbr**. that will replace the grub code on the hard drives MBR with code loading the MS boot loader ntldr.  That should get the computer to boot windows when the external is detached (or attached).  (also have heard the [Super Grub Disk  ]("http://forjamari.linex.org/projects/supergrub/") can restore the MBR to boot windows).

use a live cd or Super Grub CD and install grubs stage1 program to the MBR of the external drive.  good stuff on grub and how to use it here. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

