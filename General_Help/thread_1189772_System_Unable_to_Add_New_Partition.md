---
title: "System Unable to Add New Partition"
date: 2009-06-17
forum: General Help
---

### Post by darknight1726 on 2009-06-17
[FONT=Tahoma]Hi to ALL, 

I just have some problems on adding partition on laptop. 

Here's the exact scenario and command outputs:

1. List partition table.
[root@himura ~]# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c8ff6e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        5112      103424   83  Linux
/dev/sda3            5113        6418    10485760   83  Linux
/dev/sda4           10074       11461    11149110    5  Extended
/dev/sda5           10074       10204     1052226   82  Linux swap / Solaris
/dev/sda6           10205       10216       96358+  83  Linux
/dev/sda7           10217       11461    10000431   83  Linux

2. Try to add partition. 
[root@darknight ~]# fdisk /dev/sda

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c8ff6e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        5112      103424   83  Linux
/dev/sda3            5113        6418    10485760   83  Linux
/dev/sda4           10074       11461    11149110    5  Extended
/dev/sda5           10074       10204     1052226   82  Linux swap / Solaris
/dev/sda6           10205       10216       96358+  83  Linux
/dev/sda7           10217       11461    10000431   83  Linux

Command (m for help): n
**No free sectors available :(**

Command (m for help): 

Can anybody help me to solve this problem. Right now, reinstallation is not an option. :)

Regards, 

darknight1726


[/FONT]

---

### Post by Dysport on 2009-06-17
Why don't you use gparted or qtparted?

---

### Post by mcduck on 2009-06-17
The only free space you have on that disk is between sda3 and sda4 (The extended partition).  Since you already have 3 primary partitions and one extended you can't create a new primary partition. And since the space available is outside of the extended partition, you can't create a new logical partition either..

So, what you'll actually have to do is to resize the extended partition (sda4) to use all available space, and then you should be able to create a new logical partition inside the extended one.

(remember, only 4 primary partitions or 3 primary ones and one extended is possible. Any additional partitions have to be logical ones and inside the extended partition.)

---

### Post by Dysport on 2009-06-17
That was sort of my point: If you used a GUI partitioner app like gparted you'd have seen that in a matter of seconds (now I don't know about you, but I'm just too lazy to look at all those numbers :p)

---

### Post by m4tic on 2009-06-17
Format disk

---

### Post by Dysport on 2009-06-17
> **m4tic said:**
> Format disk

thank you very much for this :D

---

### Post by anaconda on 2009-06-17
> **mcduck said:**
> The only free space you have on that disk is between sda3 and sda4 (The extended partition).  Since you already have 3 primary partitions and one extended you can't create a new primary partition. And since the space available is outside of the extended partition, you can't create a new logical partition either..

So, what you'll actually have to do is to resize the extended partition (sda4) to use all available space, and then you should be able to create a new logical partition inside the extended one.

(remember, only 4 primary partitions or 3 primary ones and one extended is possible. Any additional partitions have to be logical ones and inside the extended partition.)

That is correct, except there seems to be free space also after the extended partition. The last used cylinder was 11461, and the last cylinder on the disk was 19457, so lots of space there too....

I would recommend qparted run from liveCD, because it can resize linux partitions..

AND remember that the numbering of your partitions will change if you add a new partition to the middle... So if you don't use uuid:s in your fstab, then your system wont automount everything it used to, or wont even boot.
But probably you do use uuids, so no problem there.

---

### Post by mcduck on 2009-06-17
> **anaconda said:**
> That is correct, execpt there seems to be free space also after the extended partition. The last used cylinder was 11461, and the last cylinder on the disk was 19457, so lots of space there too....

I would recommend qparted run from liveCD, because it can resize linux partitions..

Oh, that's true. I didn't even look at the size of the disk and just checked the partitions. :D

But the same still applies, the extended partition must be resized to contain the available disk space and all new partitions must be inside the extended one.

---

