---
title: "Couple basic questions"
date: 2009-01-06
forum: General Help
---

### Post by killbydemons on 2009-01-06
I just have a couple questions, more like concerns I had with windows, and I wonder if they exist with Ubuntu. One is that hard drive fragmentation was something I tried to stay on top of, I bought Diskeeper to make sure my drives were always defragmented.  Do I have to worry about this with Ubuntu, and if so, what options are there for defragmenters?

My other question is in windows there was a page file whose size could be altered, or it could be disabled completely.  Does something similar exist in ubuntu, and can i modify/disable it?

thanks

---

### Post by 73ckn797 on 2009-01-06
> **killbydemons said:**
> I just have a couple questions, more like concerns I had with windows, and I wonder if they exist with Ubuntu. One is that hard drive fragmentation was something I tried to stay on top of, I bought Diskeeper to make sure my drives were always defragmented.  Do I have to worry about this with Ubuntu, and if so, what options are there for defragmenters?

My other question is in windows there was a page file whose size could be altered, or it could be disabled completely.  Does something similar exist in ubuntu, and can i modify/disable it?

thanks


No need for defrag in Ubuntu (see other posts that explain this)

Ubuntu creates a "swap" partition on the hard drive for the same purpose. Generally equal to or 1.5 times larger than actual RAM. (ie ... 2Gib Ram = 3Gib swap)

---

### Post by tuxxy on 2009-01-06
> **killbydemons said:**
> I just have a couple questions, more like concerns I had with windows, and I wonder if they exist with Ubuntu. One is that hard drive fragmentation was something I tried to stay on top of, I bought Diskeeper to make sure my drives were always defragmented.  Do I have to worry about this with Ubuntu, and if so, what options are there for defragmenters?

My other question is in windows there was a page file whose size could be altered, or it could be disabled completely.  Does something similar exist in ubuntu, and can i modify/disable it?

thanks


The ubuntu default ext3 filesystem does not require you to defragment your drive. Unlike NTFS, the ext3 filesystem locates your files in different parts of the drive so files do not tend to get defragmented as much.  Also, the system will run a disk check every regularly at bootup and it helps address any problems.  If you run the following in a terminal, you can see how many times the drive has been mounted, and when the next fsck will be.

```

sudo tune2fs -l /dev/sda1
```

You will have to replace the "sda1" for the drive/partition you want to view.

 There are defragmentation tools for this filesystem, but it should not be necessary.

The page file I think you may want to read up about the swap partition.

---

### Post by killbydemons on 2009-01-07
ah, okay thanks for the info everyone.

---

