---
title: "Partion a hard drive"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-17
Hello

I just got a hard drive today for my birthday!  I need to know how to partion the hard drive.  I need to set it as active.  Is there a way to do this in ubuntu.  Or should I put it my brothers inclosure and do it on windows?  

Thanks

---

### Post by gauntalus on 2006-09-17
You certainly can partition your hard drive using Ubuntu.  Once you 've installed the hard drive, boot into Ubuntu and bring up a terminal.

First you need to figure out which device name has been given to your hard drive.  You need to use the fdisk command, on my machine the results look something like this:
```

thor ~ # fdisk /dev/hda

The number of cylinders for this disk is set to 15017.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           5       40131   83  Linux
/dev/hda2               6          68      506047+  82  Linux swap / Solaris
/dev/hda3              69       15017   120077842+  83  Linux

Command (m for help):

```
Once you've figured out which device name its been assigned, (in this code snippet, my hard drive is assigned /dev/hda), then you can use fdisk to format it.  If your drive is a SATA drive, then it will probably be something like /dev/sda or /dev/sdb.  Just make sure you figure out the correct device before you format it so you don't clobber your ubuntu install :)

From there you should be able to use the help menu (type m and press enter), or by reading the fdisk man pages, e.g.:
```
thor ~ # man fdisk
```

---

