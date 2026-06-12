---
title: "Partitioning question with /home"
date: 2007-12-14
forum: Dell  Ubuntu Support
---

### Post by realillusions on 2007-12-14
Hello all,

I'd like to move /home to a seperate partition (mostly because I need to reinstall my system, but also for the extra protection it can afford), however I'm running on one of the pre-installed systems from Dell. This affords a problem because they come with 6 partitions, and I'm not really sure which partitions are which, much less which I can resize.

the output from sudo fdisk -l gives me this:


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10         271     2104515    b  W95 FAT32
/dev/sda3   *         272         296      200812+  83  Linux
/dev/sda4             297       19457   153910732+   f  W95 Ext'd (LBA)
/dev/sda5             297         617     2578401   82  Linux swap / Solaris
/dev/sda6             618       19457   151332268+  83  Linux
```

I would imagine that /dev/sda4 or /dev/sda6 are the drives I'm looking to resize, but I can't be sure.

(Ideally, I'd just wipe my machine clean and make a fresh install with just the necessary 2 partitions + /home, but I've seen that there's a lot of trouble doing that on the Dell pre-installed machines...)

Thanks!

---

### Post by kuja on 2007-12-14
Well if you don't need the Media Direct Partition or the Restore partition, you could just ditch those if you wanted, then move/resize other things. 

Partitions 3, 5, and 6 are Linux related in some way or another, you could probably get a more readable printout using "sudo parted /dev/sda print" (It prints out in bytes instead of blocks ... and the actual partition type instead of a code that references it ..... 

Also, to see if which of them are in use, look at your /etc/fstab .... if you don't see it listed there then you don't need it to run Ubuntu ... simple as that. Anyhow, have fun, later.

---

### Post by maybeway36 on 2007-12-14
sda5 and sda6 are inside sda4.

---

### Post by gbrainin on 2007-12-14
FYI, a description of the default partitions is at [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions").

If you want to make minimal changes to the system, you should shrink sda6, create an sda7, then you can have 6 be / and 7 be /home.  I did that, following the instructions here: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome").

---

