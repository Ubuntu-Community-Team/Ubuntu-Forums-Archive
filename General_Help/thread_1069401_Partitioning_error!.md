---
title: "Partitioning error!"
date: 2009-02-13
forum: General Help
---

### Post by agim on 2009-02-13
I was trying to resize a partition and install a new OS when the liveCD froze, I waited a while then did a hard shutdown. Needless to say, things are a little screwed up.

Here is the output I get from GParted, now that I am trying to remove the new partition (which was successful) and resize the old partition to its original size.

e2fsck -f -y -v /dev/sda1

The filesystem size (according to the superblock) is 4454013 blocks
The physical size of the device is 3173888 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes


Hopefully someone can give me an answer on this tonight.
Thanks!

---

### Post by caljohnsmith on 2009-02-14
How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d

```

---

