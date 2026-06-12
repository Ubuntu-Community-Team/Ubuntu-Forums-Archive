---
title: "Formatting problem"
date: 2009-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fieryindian on 2009-01-04
Hi everyone!
I recently bought a dell studio 1537 and have wiped out vista and installed xp. i have created partitions for installing ubuntu, which are the last 2 partitions, one for ubuntu and the other for swap, on the extended logical drive. the live cd runs properly without much problems, although after some time the keys stop working.
The real problem is whenever i try to format the partitions for ubuntu to ext3, i get the following error "cannot format /sda# to ext3. The device apparently does not exist".

Can anyone help me with this?
thanks in advance.

---

### Post by natehall on 2009-01-04
Sda is usually a memory stick or something like that. To format the hard drive it should be hda. By the way if you do format a memory stick to ext3 the computer will act likes the stick is invisible! Try this command and post the results here.

sudo fdisk -l

This will list all your partitions.

---

### Post by armandh on 2009-01-04
I do not pre make the Ubuntu partitions.
rather I leave the space for Ubuntu unpartitioned.
Installing Ubuntu I select from the partition menu;
"use largest unpartitioned space"
Ubuntu is installed to a root ext3 partition and a swap partition is created. 
both are in a new extended partition. 
grub works perfectly.

xp does not play well with other primary active partitions.

.

---

### Post by fieryindian on 2009-01-05
Thanks a lot for the responses. Really appreciate! :)

Nathall - I too observed that hda should be the one shown instead of sda. But all my windows partitions too are being shown as sda. It might be so since this is a laptop. I'm just guessing.
"
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        1320    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1321       38912   301957740    f  W95 Ext'd (LBA)
/dev/sda5            1321        3870    20482843+   7  HPFS/NTFS
/dev/sda6            3871        6420    20482843+   7  HPFS/NTFS
/dev/sda7            6421       10244    30716248+   7  HPFS/NTFS
/dev/sda8           10245       14068    30716248+   7  HPFS/NTFS
/dev/sda9           14069       17892    30716248+   7  HPFS/NTFS
/dev/sda10          17893       19167    10241406    7  HPFS/NTFS
/dev/sda11          19168       22991    30716248+   7  HPFS/NTFS
/dev/sda12          22992       26815    30716248+   7  HPFS/NTFS
/dev/sda13          26816       31914    40957686    7  HPFS/NTFS
/dev/sda14          31915       33812    15245653+   7  HPFS/NTFS
/dev/sda15          33813       34833     8201151    7  HPFS/NTFS
/dev/sda16          34834       38836    32154066   83  Linux
/dev/sda17          38837       38912      610438+  82  Linux swap / Solaris
"

Armandh - The thing is that since this is a new laptop, most of the partitions do not yet have data in them. I dont want linux to partition all that space and use it for itself. :D
Else I would've done what you have done.

---

### Post by armandh on 2009-01-05
even if the partitions are empty and there is unpartitioned space no partitioned space will be used when "use unpartitioned space is selected if all the space is partitioned reduce one by about 10 G

or if there is unpartitioned space more than you want to use 

try putting in one that uses all but 10 gig and remove after
you load to the unpartitioned space

I recommend the parted magic
a live disk where you get a much better view of what is happening.

---

