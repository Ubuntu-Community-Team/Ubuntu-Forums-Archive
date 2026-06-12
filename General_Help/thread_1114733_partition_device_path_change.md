---
title: "partition device path change?"
date: 2009-04-03
forum: General Help
---

### Post by candtalan on 2009-04-03
I have a hard drive I use for keeping data on (ext3). It began life with several partitions on it, however I then changed the partitions using gparted so as to delete all but my main data partition which was sda3 and to resize, move,  this to fill the drive.

This all went ok, however I notice that the partition retains its path as
/dev/sda3
which I do not fully understand because it is now the only partition on the drive.

I am using 8.04.2

The drive automounts ok. Gparted indicates the partition as /dev/sda3.
When mounted, the mount command shows
/dev/sda3 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

It looks like it is all working perfectly although I am uneasy about what seems to be an unconventional partition name - it is now the first and only partition on the drive, and has a name of a third partition.

1) can I change the path somehow to /dev/sda1
2) are there any bad implications aside from my possible future confusion, with leaving it alone?

tia

---

### Post by lloyd_b on 2009-04-03
This is quite normal.  The "sda?" does *not* change when other partitions are added/deleted, by design (otherwise, adding or deleting an unrelated partition could make fstab entries using the older device entries instead of UUIDs incorrect).

I wouldn't worry about it.  And AFAIK, the only way to get it to "sda1" would be to completely clear the partition table (wiping the disk in the process) and then creating a new partition on the disk (though it *should* be possible to do this via some low-level editing of the partition table, I'd strongly recommend against even trying this unless you know exactly what you're doing!).

Lloyd B.

---

### Post by candtalan on 2009-04-03
thanks, I will relax.....

---

### Post by hyper_ch on 2009-04-03
well, there has been a bug when you have IDE and SATA drives... it kept changing designations regurarly on my computer. For that reason you address the devices by the UUID and not /dev/sdX

---

