---
title: "Wrong partition size after Gparted resize"
date: 2009-06-18
forum: General Help
---

### Post by zahtar on 2009-06-18
Hello all!

I run a dual boot with xubuntu 8.04.1 LTS and ubuntu 9.04. 

Initial installation for xubuntu was on a partition of 4GB, runs generally ok, but lately got 80% full. So, using the ubuntu 9.04 partition I ran Gparted and resized the Xubuntu partition from 4GB to about 10GB.

Now, booting into ubuntu I see the xubuntu partition as a "11GB media" which I can mount read and write to. Booting into xubuntu, it still sees its own partition as 4GB and reletively full. 

How can I tell xubuntu that, "*hey, your partition is larger now, use all the space you have here"*?I see in the *System Monitor* that it starts using the swap too.

thnx in advance

---

### Post by WatchingThePain on 2009-06-18
Hi,
When you use gparted the live cd is best.
When you make a partition larger then other partitions get moved and shrunk.

Post output from 

> sudo fdisk -l

---

### Post by zahtar on 2009-06-19
thnx 4 your reply :)

I removed a logical partition so that made for room for sda5 (xubuntu 804) which I increased as I described in the first post.
The ubuntu 904 partition is obviously sda3.

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               3        1341    10755517+   5  Extended
/dev/sda2            2709        2839     1052257+  82  Linux swap / Solaris
/dev/sda3            2840        4751    15358140   83  Linux
/dev/sda4   *        4752       14593    79055865    7  HPFS/NTFS
/dev/sda5   *           3        1341    10755486   83  Linux

```

---

