---
title: "How to delete partition on software RAID array"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Adrayic on 2006-09-30
I have a software RAID 5 (configured w/ mdadm) array formatted with one EXT3 partition.  I want to switch this to a XFS partition.  Do I need to delete the EXT3 partition before I can run mkfs.xfs?  If so, how do you delete it?  The drive is empty so there is no fear of loosing information :)

---

### Post by Ocxic on 2006-09-30
you can just unmount the raid partiton and run mkfs.xfs on the partition ex:

sudo mkfs.xfs /dev/md?

---

### Post by Adrayic on 2006-09-30
Thanks.. I just ran it but I had to use the -f option to force overwrite of the EXT3 partition.  Everything seems to be good.  I was able to mount the partition and I can write to it so I think all is well.  I guess only time will tell.  

One more question -- how do I make more partitions on the array?  I ran the mkfs.xfs command and I got one big partition spanning the entire array.  Is there a way to make multiple partitions instead of 1 big one?  Thx

---

### Post by lha on 2006-10-01
> **Adrayic said:**
> Thanks.. I just ran it but I had to use the -f option to force overwrite of the EXT3 partition.  Everything seems to be good.  I was able to mount the partition and I can write to it so I think all is well.  I guess only time will tell.  

One more question -- how do I make more partitions on the array?  I ran the mkfs.xfs command and I got one big partition spanning the entire array.  Is there a way to make multiple partitions instead of 1 big one?  Thx

[Debian bootable/partitionable RAID1 MICRO-HOWTO]("http://www.miquels.cistron.nl/raid/")

It's for Debian, but should work for Ubuntu, too.

---

