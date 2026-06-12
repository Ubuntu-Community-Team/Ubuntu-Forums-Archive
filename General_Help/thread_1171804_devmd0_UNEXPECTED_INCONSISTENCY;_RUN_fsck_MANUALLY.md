---
title: "/dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY"
date: 2009-05-27
forum: General Help
---

### Post by baeda on 2009-05-27
Hi all,
due to a loss of power, 8.04 does not boot anymore:
I configured a RAID 1 using two Seagate 250 HDDs, 4 partitions: md0 - md3.

After this loss of power, i get the message when booting:
/dev/md0: The filesystem size (according to the superblock) is 2441872 blocks
The physical size of the device is 2441856 blocks
Either the superblock or the partition table is likely to be corrupt!

/dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
fsck died with exit status 4

so far, what I tried: I didn't succeed using a boot CD with ubuntu: caus its a raid, I cant access sda1, and /dev/md0 will exit with device not found.

I also tried to resize fs (sudo resize2fs /dev/md0), unfortunately, its mounted (/).

There was an interesting post from blader_se: [http://ubuntuforums.org/archive/index.php/t-339356.html](http://ubuntuforums.org/archive/index.php/t-339356.html), but I can't rename or remove blkid.tab, as filesystem is in read only mode. 

any idea what I can try else? thanks in advance! Peter

---

