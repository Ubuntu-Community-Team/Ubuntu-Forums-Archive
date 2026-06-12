---
title: "Resize / how?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2005-10-17
Hey ya'll. 

Question; I have a 20 gig hd currently partitioned:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2432      730957+   5  Extended
/dev/sda5            2342        2432      730926   82  Linux swap / Solaris

I want to resize the empty space (About 9 gig) to a /home partition and then set it up as my /home partition.  I've seen another how to on this, so I can setup the fstab etc, no problem.  My primary question is how to do I resize the partition (or how to do I boot from the rescue disk and resize) and what not.  I can sort of use fdisk, although I'm more keen on cfdisk.  

I really don't want to break my system setup...

Thanks

Aaron

---

### Post by hw-tph on 2005-10-17
The quickest and easiest way is probably using something like [SystemRescueCD](http://www.sysresccd.org/index.en.php) to boot and run QtPartEd (a Partition Magic wannabe that works well enough in most cases).

As always, don't forget to back up your system. You have been warned.


Håkan

---

