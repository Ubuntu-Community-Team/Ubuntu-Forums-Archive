---
title: "Root Partition full, inaccessible installation - Please Help!"
date: 2009-03-09
forum: General Help
---

### Post by kneewax on 2009-03-09
aaaaaaaarrrrrrggggggghhhhhhhh!

My 1st HDD is partitioned so:

1 x root partition 
1 x $home partition
1 x data partition

I also have a second disk is currently empty, as I have only just installed it and was planning to use for media files and a system backup.

Not sure what caused it, but my root partition has been completely filled.  I cannot access the installation as the Gnome won't load and command line login fails.

I have booted the Live CD and attempted to create more space by mounting the root partition and seeing if I could move or delete some data - but it won't mount.

I then thought I might be able to create some space by resizing the partition, but despite making room by resizing and moving the other partitions on the disk, I am unable to expand the root partition into the unallocated space.

Please if anyone has any ideas that might help I'd be very grateful.

---

### Post by stanz on 2009-03-09
Aside from the livecd, have ya tried gparted?
gparted doesn't mount anything - so resizing has been successful allot.

if ya google around here and check the wiki - ya might find other methods from users in similar jams.

hope this helps ~ ;)

---

### Post by kneewax on 2009-03-09
> 
I then thought I might be able to create some space by resizing the partition, but despite making room by resizing and moving the other partitions on the disk, I am unable to expand the root partition into the unallocated space.

Please if anyone has any ideas that might help I'd be very grateful.

This I did with gParted.  I  now have space at the end of the disk, but gParted won't let me move the logical partition to the right so I can extend the primary into the unallocated space!

Googled answers don't seem to cover this set of circumstances.  there is not one free byte  on the primary  partition.

---

