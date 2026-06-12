---
title: "Alert! /host/ubuntu/disks/root.disk does not exist"
date: 2009-01-15
forum: General Help
---

### Post by SomeWhoCallMeTim on 2009-01-15
I downloaded the latest wubi.exe and installed wubi on my Windows XP box (Service Pack 3). The iso downloaded was ubuntu-8.10-desktop-i386.iso.

I have two disks on my machine, each of which has two partitions:

C:, D:, and H:, I:.  H/I was my old smaller boot disk that I kept connected as a backup. I boot Windows XP off of C:.

The Wubi installer offered the choices of installing on D: or I:. (I don't have enough room on C:).

I selected D: from the wubi menu dropdown and when it completed (and before rebooting) verified that it created a wubildr and wubildr.mbr on D: as well as a ubuntu directory.

When I rebooted I selected ubuntu from the boot menu. It apparently installed correctly (I got the progress bar, etc.) and then it rebooted. I selectd ubuntu from the boot menu again and I got the following error and it dumped me into BusyBox.

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to shell!

Interestingly, if I do an ls /host I can see that /host is pointing to the I: drive and not the D: drive where the root.disk is located.

Somehow the ubuntu is confused and is looking for the root.disk on I: (where it does not exist) rather than D: (where it does exist).

The Windows XP boot.ini has the following in it:

c:\wubildr.mbr="Ubuntu"

which is interesting since I told it to install on D: and not C:

Any ideas on what I can do to fix this?

Thanks!

---

