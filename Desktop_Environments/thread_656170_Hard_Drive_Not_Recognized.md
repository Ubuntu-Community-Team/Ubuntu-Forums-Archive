---
title: "Hard Drive Not Recognized"
date: 2008-01-02
forum: Desktop Environments
---

### Post by TimTow on 2008-01-02
Here is the problem:

I have two SATA internal hard drives (320G).  I can only save information on the first hard disk, the one that my OS is on.  The second drive, I cannot save to, but my computer kind of knows that it is there.  

My mother board has 6 SATA ports.  I have both hard drives connected through the 1st and 2nd port.  The problem is that in my BIOS both hard drives are detected and functioning.  But when I boot-up, and I go to filesystem, my capacity is limited to the first hard drive, port 1.  My OS doesn't know I have another hard drive attached, or it doesn't display it as an option to save information to.  I have opened up a terminal and tinkered with it...no avail.  

I have determined through terminal information that the first hard drive is labelled sda connection with 3 separate partitions.  I have determined that the second Hard drive, the one I want my computer to recognize, is sdb, but there are no sdb partitions.  

Ultimately, I only have 1/2 the capacity I am looking for.  Does anybody know of a code I can put in to get Ubuntu 7.10 to recognize my second hard drive?  I tried formatting the device and it said permission denied!  I might not be using the proper formatting command?

---

### Post by jken146 on 2008-01-02
I take it Ubuntu detects the device.  That is, it shows up when you type ```
sudo fdisk -l
```

An easy way of creating a partition and formatting it is with gparted.  It's in the repositories.

---

### Post by TimTow on 2008-01-02
yes.  When I type in the command:

sudo fdisk -l 

in the dev directory, it spits out this:  


"Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed9a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38161   306528201   83  Linux
/dev/sda2           38162       38913     6040440    5  Extended
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table"


So, it clearly is there and detected, but how do I partition the drive?

---

### Post by TimTow on 2008-01-02
when I type in:

gparted sdb

it says: 

gparted is only allowed in the root, as it can be a weapon of mass destruction.  


....almost there

---

### Post by TimTow on 2008-01-02
sudo gparted sdb

opens a window that says in the bottom left corner:

device not detected

---

### Post by TimTow on 2008-01-03
thanks, I figured it all out, got gparted installed, created a partition on that hard drive and have the full capacity now available to my system.  Much obliged.

---

