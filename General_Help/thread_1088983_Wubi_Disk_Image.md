---
title: "Wubi Disk Image"
date: 2009-03-06
forum: General Help
---

### Post by Agg23 on 2009-03-06
When I installed Ubuntu using Wubi I only gave it 10GB.  I would like to increase the disk image.  I have tried both way that are suggested in the Wubi Guide and they didn't work.  I have created a new disk image, I just need a way to copy the files from the old image to the new one.

---

### Post by martrn on 2009-03-06
Loopback devices
----------------

Loopback devices in the Linux hardware system allow for the "emulation" of a block device (a CD/DVD-ROM drive, a hard drive, etc).  Loopback devices are most commonly used for two things:

    * Mounting filesystem images (such as .iso CD images or ext2 disk images)
    * filesystem encryption through the use of the CryptoAPI and cryptoloop device. 

An example of mounting an vdisk image via loopback:

    sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

In Windozs, you need/areforced to run a program to read the vdisk file. In Linux, the code has already been written in the kernel to read the various disk formats. 

If you visit [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

If you scroll down to the section where it says How can I access my Wubi install and repair my install if it won't boot?  Then it describes how to mount your virtual disks under any version of ubuntu weather it be the webi version, the live cd version or an installed hdd version.

Added.
------

You can mount 2/3/4/5/6 or more versions of any disk image and use the terminal command cp to copy files from one disk image to another.

---

### Post by Agg23 on 2009-03-09
I tried your suggestion, but it didn't work. :(

---

