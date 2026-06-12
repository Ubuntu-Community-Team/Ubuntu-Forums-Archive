---
title: "Having trouble partitioning..."
date: 2006-01-01
forum: General Help
---

### Post by Mazin on 2006-01-01
I had a drive that was split with almost all of it Ext3, and 500 mb as swap.

I wanted to shrink the Ext3 partition by about 10 GiB and create a FAT32 partition with the free space.

However, after using GParted from the Ubuntu Live disc, I couldn't get it to work.  I would tell GParted to resize the Ext3 partition, and it would appear to be doing so.  When it's done, I look and nothing has changed.  How can I resize that partition?

---

### Post by zoiks on 2006-01-01
Good question.  Did you try checking the partition table after a reboot?  I've always gotten the message from fdisk that the new partition information won't be re-read by the kernel until a reboot.

---

### Post by Mazin on 2006-01-01
Yep, I tried Refreshing GParted's info and rebooting.  Does it have something to do with the fact that the ext3 partition is flagged as bootable?

---

### Post by Omnios on 2006-01-01
I think its becuase the partition can not be moutned when resising or partitioning therefor you will probably have to get the knopics cd gtparted thingy and do it for there though im not familiar with the dc

---

### Post by canadianwriterman on 2006-01-01
Just install qtparted (available on Synaptic) and use it instead of gparted. You still need the ntfsprogs plug in for qtparted to work. I tried both and qtparted was the only one that worked.

---

### Post by az on 2006-01-01
You need to unmount your swap.  The live cd mounts it automatically.

---

