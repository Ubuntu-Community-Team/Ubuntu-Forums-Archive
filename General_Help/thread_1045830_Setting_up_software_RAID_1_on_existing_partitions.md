---
title: "Setting up software RAID 1 on existing partitions"
date: 2009-01-20
forum: General Help
---

### Post by Simetrical on 2009-01-20
I have two disks now, /dev/sda (160 GB, boot disk, data on /dev/sda1) and /dev/sdb (80 GB, data on /dev/sdb2).  I just got a new 500 GB disk.  What I want to do is set up two new partitions on the new disk (which I'll refer to as /dev/sdc), and turn /dev/sda1 + /dev/sdc1 into /dev/md0, and /dev/sdb2 + /dev/sdc2 into /dev/md1, i.e., mirror my existing partitions using software RAID.  (Of course the performance here won't be great, but I mainly just want to be able to survive a disk crash.)

I would like to do this without having to wipe or significantly alter my existing partitions.  What I'm imagining is doing some procedure (from a Live CD) to tell Linux to construct /dev/md0 from /dev/sda1 and "missing", without touching existing data, then add /dev/sdc1 and rebuild the mirror.  I don't see why this shouldn't work, with mirroring (obviously it won't work with striping).  But does anyone know if it's possible?  Everything I've seen seems to assume that when you build the array, you wipe the contents of the partition.

If it's not possible, what procedure would you recommend that minimizes my chances of messing up and losing data?  Copy the existing partitions to free space on the new disk, wipe the old partitions and set up RAID, copy back the partitions?  What's the fastest and/or most lossless way to copy partitions?  (Will special things like named pipes and whatever survive tar?)

Thanks for any help.

Edit: [This](http://tldp.org/HOWTO/Boot+Root+Raid+LILO-4.html) is somewhat dated, but gives an approach that takes one less copy than my second choice: create /dev/sdc1 and /dev/sdc2 as empty RAID1 partitions with the mirror missing, cp -a from the old partitions (or perhaps copy using parted or something), then set the old partitions as missing and rebuild.  This is scary because if something goes wrong, I guess my system will be unbootable, but maybe I'll just have to live with that.

---

