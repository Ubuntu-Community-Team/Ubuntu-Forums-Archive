---
title: "Duel Boot, Duel Raid problems."
date: 2006-01-06
forum: General Help
---

### Post by thessem on 2006-01-06
I own two 80G IDE hard-drives, and I wanted to install both Windows and Ubuntu on them (And before you start going all elitist linux on me, I really need that windows install). I figured having them in software raid 0 would make them alot faster (I dont have any raid cards, and I cant be bothered with on-board raid things on the mobo)

I installed windows on a small 3g partition, just small enough to fit a normal install. I converted both harddrives to "Windows Dynamic Disks" (the LDM in the linux kernel seems to be able to write and read to them in linux from what i've read), Then I made a small 3g partition on hdb, as a sort of place holder for a 500meg /boot directory and a 2.5gig fat32 fileswap that both OS' can read/write to.

I created a 30G partition on both drives and formatted them to ntfs, and put them to raid 0, then two more 40g partitions, raid 0 and ntfs (Linux would reformat them later) and the same thing for 2 1gig partitions on the last part of the hard drives (swap, and since they are on the outside of the HD platter, and on raid0, its gonna be nice and fast)

Enter the ubuntu.

The ubuntu install went normally, until I got up to the part with the partitioning. I went command line, ran 

```
modprobe md
``` (multiple disk driver)
```
mdadm --create /dev/md/0 /dev/hda3 /dev/hdb3 -n 2 -l 0 -c 64
``` (My nice big raid / drive)

```
mdadm --create /dev/md/0 /dev/hda3 /dev/hdb3 -n 2 -l 0 -c 64
``` (My nive fast swap)

and it set them up alrite, so I formatted them and set the mount points as normal and then I installed.


My problem here is that the ubuntu partitioner didnt see the partition I set aside for /boot. The reason that this is a problem, is that I'm doing software raid here, and I need lilo and the kernel in a non-raid partition so the kernel loads, and recognises the raid.

The partitioner didn't acually see any partitions at all, just two 80g harddrives. I have an entire operating system installed in a raid partition, but no way to boot it.

Is there any way I can use a partitioner that supports moth md (multiple disks) and LDM (Logical Disk Manager, windows dynamic disks), and partition hdb1 to ext3, or anything, install lilo on it and boot off it?

I'm looking at some windows software at the moment "Paragon Partition Manager) to see if that works, but is there any way I can do this for free, or even using gpl?

Thanks.

Ps. Do you think if I get this working using free tools, anybody would be interested if I bothererd to write up a proper Ubuntu tutorial for what I'm doing?

---

