---
title: "Partition Table Erased - How'd I manage that?"
date: 2009-04-05
forum: General Help
---

### Post by Roasted on 2009-04-05
I'm a little confused here. I was trying to image a spare computer I have here. As a curve ball, I was throwing in different sized hard drives to test the software's ability to resize the partitions on the fly as they are imaged.

The one drive I put in came back as "Can't have a partition outside the partition table!"

I was like, whoa, what do I do here? I know the drive works, but I had no idea why I got that error.

I popped in a GParted CD and created a new partition on the disk. Or so I thought. When I hit new, it told me if I continue everything on the disk will be erased. Okay fine, so I hit create. But after I did that, the disk was still 100% unallocated, an indication to me it had written the partition table to the disk.

I rebooted, set up the image process again, and now it worked. So somehow I lost my partition table.

I'm curious to know how I could have done that. Does GParted have the ability to erase the partition table? I'm not sure how else I would have done such a thing.

Note - everything is working fine now. I'm just that darn curious I want to know what happened. Thanks!

---

### Post by jimreynold2nd on 2009-04-05
Hmm... maybe that disk had another partitioning scheme on it (i.e. probly GUID and not MBR).

---

### Post by Roasted on 2009-04-05
I think I know what happened.

I'm using FOG as my image software which is linux based. It has the option to wipe the disks. I just tested it and when I wipe a disk with it, it wipes the partition table too. Popped in GParted, created the table, and bam I was ready to image then.

I just wanted to know what caused it so I don't make that happen when I have a lot of computers to do with only a little bit of time to do it in. I don't want to pop a CD in a couple hundred computers simply to create a partition table. Ha!

---

