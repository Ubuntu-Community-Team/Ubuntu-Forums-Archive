---
title: "Resizing my NTFS partion - partition gone!"
date: 2006-08-25
forum: Desktop Environments
---

### Post by toml0006 on 2006-08-25
I tried running the installation off of the live DVD and did a manual resize of my main disk (which has 1 NTFS Windows partition) and opted to create 2 new partitions - 1 ext3 and 1 linux swap for a grand total of 3 partitions:

NTFS ~150GB
ext2 ~6GB
swap ~4GB

The operation completed without any visible error, but now the disk manager shows that the whole disk is unformatted.  

fdisk -l shows:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321   82  Linux swap / Solaris
/dev/hda2           19458       19458           0+  83  Linux
/dev/hda3           19458       19458           0+  83  Linux


I have some important data on this partition (I know i should've backed it up - I'm kicking myself) that I don't want to loose.  I am running:

gpart /dev/hda1

right now (2+ hours and still says Begin scan...), is there anything else I can do to get access to my files?

---

