---
title: "fsck.ext3 no such file or directory"
date: 2006-08-16
forum: Desktop Environments
---

### Post by doc_holiday on 2006-08-16
When booting I get:

Checking all filesystems...
fsck.ext3 no such file or directory while trying to open /dev/hdb
/dev/hdb:
The superblock could not be read or does not descrive a correct ext2 filesystem. If the device is valid an di really contains an ext2 filesystem, then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 (device)


Any idea what I can do? hdb contains ext3 filesystem.

---

### Post by lamego on 2006-08-16
/dev/hdb refets to a disk, not to a partition, partitions names must have numbers.
Please check for the available partitions with:
sudo fdisk -l

---

### Post by doc_holiday on 2006-08-16
problem looks solved, I rebooted 2 times before posting here. Then shut down the pc. Now I wanted to do the fdisk and it just booted normally. 
This looks like windows :(

---

