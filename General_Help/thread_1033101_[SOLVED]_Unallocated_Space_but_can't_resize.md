---
title: "[SOLVED] Unallocated Space but can't resize"
date: 2009-01-07
forum: General Help
---

### Post by leveliv on 2009-01-07
I have my 250 gig harddrive, I recently had vista installed on a 150 gig partition then the rest was Linux now I recently ran out of space on the linux partition and I had taken quite a liking to linux so I deleted it from the live CD but when I went to resize the partition of the linux it would only let me add like 3 mb the Free space is before the Linux partition not after..if that matters.

---

### Post by linux_tech on 2009-01-07
Are you using gparted to resize?
Are you able to resize the 250 GB disk?

---

### Post by leveliv on 2009-01-07
yah I am using Gparted from the 8.04 live CD ..That probably doesn't matter. and no I can't resize anything. I can make new partitions but I dont want to do that I would rather keep my disk as tidy as possible.

---

### Post by leveliv on 2009-01-07
```
chris@chris-laptop ~ $ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4           20907       30401    76268587+   5  Extended
/dev/sda5           29417       30401     7912012+  82  Linux swap / Solaris
/dev/sda6           25161       29415    34178256   83  Linux
/dev/sda7           20907       25159    34162159+  83  Linux

Partition table entries are not in disk order
```

---

### Post by leveliv on 2009-01-07
Alright I fixed it myself. 

turns out the Swap was active still so I just 
```
sudo swapoff -a
``` 'd it and then I resized my Extended partition to add the extra 200ish gigs I had lying there. after that I just resized my home partition and it is finishing up right now. Thanks for the help.
(I failed to remember that apparently if there is a set of keys beside a partition it means its busy or active.) 
 


It's always something small like that.

---

