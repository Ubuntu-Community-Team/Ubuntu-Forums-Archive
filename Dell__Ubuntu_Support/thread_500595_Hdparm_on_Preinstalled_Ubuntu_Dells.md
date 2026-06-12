---
title: "Hdparm on Preinstalled Ubuntu Dells?"
date: 2007-07-14
forum: Dell  Ubuntu Support
---

### Post by UberIcarus on 2007-07-14
how exactly do I set up hdparm options? I mean hdparm -v and fstab both list a /dev/sda1, but there is no sda1 in /dev/, also there's no way to change the (very limited) hdparm options

Exactly where are the disks kept in the cryptic dell tripple boot thingy?

---

### Post by fjgaude on 2007-07-14
If you use something like gparted you'll see that /dev/sda1 is 16-bit FAT, sda2 is 32-bit FAT, and sda3 is Linux ext3. So hdparm can be used on all three partitions.

frank@moonlight:~$ sudo hdparm -v /dev/sda1
/dev/sda1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 112392, start = 63

Am I missing something?

frank

---

### Post by HermanAB on 2007-07-14
Hmm, most hdparm settings don't work with SATA drives.  The interface optimizes automatically and hdparm cannot really improve anything.

---

### Post by fjgaude on 2007-07-14
You have written a truth. <smile>

Still it's fun to test sdx devices, especially RAID sets:

sudo hdparm -tT /dev/md64

/dev/md64: (seagate newer RAID0 2x using mdadm Linux software RAID)
 Timing cached reads:   1516 MB in  2.00 seconds = 758.17 MB/sec
 Timing buffered disk reads:  344 MB in  3.01 seconds = 114.38 MB/sec

frank

---

### Post by UberIcarus on 2007-07-14
Well, problem being is that there is no /sda# (any of them in /dev/, running hdparm -v /dev/sda# does list a drive...but it lists all of them as being 16bit ?

---

### Post by fjgaude on 2007-07-14
> **UberIcarus said:**
> Well, problem being is that there is no /sda# (any of them in /dev/, running hdparm -v /dev/sda# does list a drive...but it lists all of them as being 16bit ?

I guess we still don't understand the issue. You mean no listing of drives in /dev/disk?

I guess that's the way it is for hdparm, showing all SATA drives as 16-bit when they are 32 or otherwise, even 8. I see the same thing on my other two computers, non-Dell, non-laptop.

What are you wishing to achieve with hdparm? I only use it for relative speed of arrays and the like.

frank

---

