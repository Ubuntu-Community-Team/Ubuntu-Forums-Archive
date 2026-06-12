---
title: "partitioning help needed"
date: 2006-02-16
forum: Desktop Environments
---

### Post by billpoo90 on 2006-02-16
Ok, here's the beef, i have 3 partitions on my HD, one ubuntu, one windoof and one empty one in ext3 format.

What i need to do is to somehow add the empty ext3 partition to my ubuntu one thus doubling the HD allocated to it.

I'm not sure how to do this, i think i need to unmount ubuntu first but again, need some advice.

Many thanks.

bil

---

### Post by wrtrdood on 2006-02-16
To make it all one partition would require removing both (as in deleting them) then creating a new one from the free space created.  Of course this obviates the need to back up the Ubuntu partition otherwise you lose everything.

An easier way is to simply create a new mount point and add that parition to the /etc/fstab file.

---

### Post by aysiu on 2006-02-16
This may not be possible if the partitions are in the order you gave them.

You can tack space on to the **end** of a partition, but not the beginning.

If it's on the end, anyway, what you want to do is delete the Ext3 partition and then resize your Ubuntu partition to fill up the rest of the space. You'll need a live CD to do this.

I recommend [using DiskDrake on PCLinuxOS](http://www.ubuntuforums.org/showthread.php?t=114142), but you can just as well use QTParted on Knoppix.

---

### Post by billpoo90 on 2006-02-16
wicked, thanks a lot, yeah, the blank one is in the middle, shall delete and resize and get hold of a live cd.

Will this affect my current install though?

---

### Post by aysiu on 2006-02-16
If it goes in this order:

1. Ubuntu
2. Blank
3. Windows

then you can add the blank space to Ubuntu by deleting it and resizing Ubuntu.

If it goes in this order:

1. Windows
2. Blank
3. Ubuntu

the only way to add that blank to Ubuntu is by deleting the blank **and** deleting Ubuntu--then reinstalling Ubuntu in the combined blank space.

---

### Post by billpoo90 on 2006-02-17
yes, it is that second lot there indeed.

Would rather not have to re-install tbh, shall have to just mount the blank partition as ext3 then.

cheers.

---

