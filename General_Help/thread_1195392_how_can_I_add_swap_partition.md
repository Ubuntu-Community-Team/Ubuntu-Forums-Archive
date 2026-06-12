---
title: "how can I add swap partition?"
date: 2009-06-23
forum: General Help
---

### Post by firsttimeuser on 2009-06-23
I thought I selected swap partition when i performed install, and just now i noticed the swap size is 0

#free -t
Swap:            0          0          0

Instead of reinstall the server, what other options do I have?

thanks

---

### Post by milton1 on 2009-06-23
use parted magic to make space on yor drive. Then create a swap partition and put a line for the swap space in /etc/fstab

---

### Post by blueridgedog on 2009-06-23
Before we assume you don't have a swap partition, what is the output of 

```
sudo fdisk -l
```

---

### Post by firsttimeuser on 2009-06-23
this is odd, how comes there are swap showing up when using fdisk?

# fdisk -l

Disk /dev/sda: 250.9 GB, 250924236800 bytes
255 heads, 63 sectors/track, 30506 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034e7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2553    20506941   83  Linux
/dev/sda2            2554        3647     8787555   82  Linux swap / Solaris
/dev/sda3            3648       16702   104864287+  83  Linux
/dev/sda4           16703       30506   110880630   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3495.0 GB, 3495029637120 bytes
255 heads, 63 sectors/track, 424913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267349  2147480811   83  Linux

---

### Post by bodhi.zazen on 2009-06-23
all you need to do is :

```
sudo swapon /dev/sda2
```

and add an entry to fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by firsttimeuser on 2009-06-23
thanks, i am printing out the links

before I read the doc, why the swap shows up in "fdisk" but not 
"free -t"

> **blueridgedog said:**
> Before we assume you don't have a swap partition, what is the output of 

```
sudo fdisk -l
```

> **bodhi.zazen said:**
> all you need to do is :

```
sudo swapon /dev/sda2
```

and add an entry to fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by blueridgedog on 2009-06-23
> **firsttimeuser said:**
> thanks, i am printing out the links

before I read the doc, why the swap shows up in "fdisk" but not 
"free -t"

fdisk listed the partitions on the hard disk drives in your system.  One was formated as a swap partition.  Free lists the memory used and since you were not using the swap partition, it is shown as 0.

---

### Post by HermanAB on 2009-06-23
the best way to figure out swap is to read the swapon man page:
$ man swapon

---

