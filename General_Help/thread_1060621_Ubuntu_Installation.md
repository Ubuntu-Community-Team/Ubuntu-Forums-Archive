---
title: "Ubuntu Installation"
date: 2009-02-04
forum: General Help
---

### Post by bigschwanz9 on 2009-02-04
I have Windows Vista but today I installed Ubuntu 7.10 on a partition using the install disk.  The problem is I don't know how to boot back into windows because it always goes straight into Ubuntu.  This would not be a problem except this is my girlfriends computer and she needs it for school tommorow, and now she has none of her windows **** anymore.

---

### Post by adult swim on 2009-02-04
go to the a terminal, Applications>Accessories>Terminal, then copy and paste the following line in there
```
sudo fdisk -l
```  hit enter, and then type in your password and hit enter.  that will return some information. copy it and paste it here.

---

### Post by bigschwanz9 on 2009-02-05
user@user-laptop:~$ sudo fdisk -1
[sudo] password for user:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
user@user-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x122cd09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1945     5855692+  82  Linux swap / Solaris
/dev/sda3            1946        4377    19535040   83  Linux
user@user-laptop:~$ 


first half is what you told me the second was me being confused.  thanks for any help.

---

### Post by adult swim on 2009-02-05
the second part was what i was after, that was a lower case L.  now for the bad news, if the computer only has one hard disk, it looks like you have overwritten windows with ubuntu.  before you freak out, you may be albe to recover some of that data with testdisk.  here is a wiki on how to get it and how to use it, i personally have never used it but others have so if you run into any problems or questions, someone should be albe to help you out.  one thing you should do is shut down the computer and only use your ubuntu live cd on there to prevent overwriting any data that you may be albe to retrieve. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by bigschwanz9 on 2009-02-05
Thanks so much, and don't miss adult swim. Lol. Peace.

---

### Post by bigschwanz9 on 2009-02-05
Hopefully you respond, but how would I extract the file on another computer if i saved the download of testdisk to a external hard drive.  The other computer is ubuntu 7.10 as well.

---

### Post by adult swim on 2009-02-05
if you have internet access on the computer that you are trying to recover, you should be able to boot the live cd and then run from a terminal ```
sudo apt-get install testdisk
```
EDIT:  if you dont have internet when you use the live cd, you can boot the live cd, and when you get to the desktop, plug in the external hard drive that you have testdisk saved on and then open that drive up by double clicking the icon that will show up on your desktop.  once you have done that drag the testdisk file to your desktop, then right click it and select extract here.  to run it youll need to open up a terminal again and enter in these commands, one at a time.
```
cd Desktop/testdisk-6.10/linux

./testdisk_static
``` 
you may get a message about needing to resize the terminal for the program to run, all you have to do is drag the edges of the terminal to make it bigger.  good luck!

---

### Post by bigschwanz9 on 2009-02-05
Yay, and then no, I don't have internet access because of the new damn internal wireless cards.  In case you have not figured it out now I'm trying to get another computer to work using my friends.  This one has only ubuntu though. :D

---

### Post by bigschwanz9 on 2009-02-05
Damn didn't scroll all the way down.

---

### Post by adult swim on 2009-02-05
i edited my previous post to tell you how to run it if you have the testdisk download on an external hard drive.  just to make sure, i think you will want to have the one that is for linux kernel 2.6.x

---

### Post by TheDumbening on 2009-02-05
You probably should've done what I did and installed Ubuntu 8.10 using Wubi. It allows a dual-boot option when you start up your computer so you can choose whether to run Windows or Ubuntu.

---

