---
title: "Partition suddenly read-only -- help"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Westerberg on 2006-03-22
I have three mounted vfat partitions.  One has recently become read-only without my approval and despite my efforts to make it writable.  Its permissions allow for full read/write/execute by all users and groups.  Despite this all files and folders on this partition are write-protected.  Whenever I try to make a change to this partition, I receive the following alert:
***[CENTER][INDENT]> Couldn't [perform intended action on file or folder] because it is on a read-only disk[/INDENT][/CENTER]***
I am able to write to the other two partitions, which are on the same physical drive as the bad partition.
Does anyone have any insight into why this problem exists?

---

### Post by dragonfyre13 on 2006-03-22
Check and see if Fstab is correct for the partition.
The wiki on my site should have an example of the correct Fstab line.


[http://www.dragonfyre13.com/TimWiki/MountFileSystems](http://www.dragonfyre13.com/TimWiki/MountFileSystems)

---

