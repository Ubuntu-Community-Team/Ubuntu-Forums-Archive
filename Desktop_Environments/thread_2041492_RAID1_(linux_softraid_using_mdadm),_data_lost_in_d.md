---
title: "RAID1 (linux softraid using mdadm), data lost in disk with data when added to RAID1"
date: 2012-08-12
forum: Desktop Environments
---

### Post by leo_m on 2012-08-12
I had two disks with dedicated data partitions which were kept in sync using periodic rsync (not RAID).  One of the disks failed.  I bought a new disk and decided to switch to RAID1 instead of using rsync to keep the data in sync across the two disks.  

Instead of adding only the new disk to a RAID1 array first and copying the data from old disk to the mounted RAID1 array device (md0, mounted on a directory inside /media directory), I thought I would just add respective data partitions on both the disks to RAID1 array and let the data be kept in sync automatically by RAID1 softraid.  This hasn't gone well.  The initial sync succeeded and finished.  But afterwards, when I attempted to mount the md0 device, it could not determine the filesystem on the RAID device (filesystem is of type 'RAID member' or similar).  I could not find a way to be able to mount the RAID device at all!

So, I started from scratch, this time adding the new disk to a new RAID1 array having two devices but with one of the two devices not yet added (marked as missing).  Then I created a filesystem on this RAID1 device (which I had not done earlier) and mounted this device.  This device is now ready to accept the data.  But my old disk's data partition which was already added to the previous RAID1 array as mentioned in previous para, is no longer capable of being mounted.  I tried to then remove the old disk's data partition from the previous array by using -r option to mdadm and then running mdadm with --zero-superblock option.  This means that the old disk is no longer mounted as RAID1 device automatically upon bootup and that's fine.  What is not so good is that I still cannot mount the old disk partition with its original filesystem.  Looks like creating a RAID1 array with the old disk's data partition has messed up existing data on that partition.  Blunder, as I lost one copy of the data through disk crash and the remaining copy of data through creating a RAID1 array with the partition containing the remaining copy of the data.  My assumption that creating a RAID1 array using a partition with existing data won't harm that data at all seems to have been incorrect.

I have now attempted to resurrect the previous superblock on the old disk partition using e2fsck with the -b block option to specify an alternative superblock but I am not confident it is going right (e2fsck gave me a warning that the size reported by the alternative superblocks (I tried more than one) is much more than the physical size); e2fsck has been running for a few hours now and I am now very apprehensive that I have lost all my data, accumulated over the past 7-8 years and containing my important VMs as well as media files (photo albums, videos, everything...).

Is there a way to salvage data from a partition which became unmountable after being added to a RAID1 array when the array was created?  Note that I may have made things worse by now running e2fsck, deleting the RAID superblock and trying to resurrect the previous ext3 superblock on the old partition.

---

