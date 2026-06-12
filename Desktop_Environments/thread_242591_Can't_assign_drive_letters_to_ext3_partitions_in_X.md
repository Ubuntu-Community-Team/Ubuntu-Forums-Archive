---
title: "Can't assign drive letters to ext3 partitions in XP despite using ext2fs"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Tom Brokaw on 2006-08-23
**Short version:**
Can see and access three ext3 partitions from XP.  Disk Management in XP does not show drive letters and will only allow me to delete the partitions.  I can access some of the drives from My Computer; these were installed before I installed ext2fs on XP.  Unable to see or access three other drives from Windows.

**Long version:**

I'm using the ext2fs to allow access to my linux drives from Windows.  I have a somewhat large JBOD array.  Here goes:

**Maxtor 160 GB:**
HDA1 - XP boot partition, NTFS
HDA2 - Ubuntu boot partition
HDA3 - Linux swap partition
HDA4 - Shared EXT3 partition, currently empty.

**Maxtor 250 gig:**
HDE1 - Ext3, contains music collection.

**Western Digital 160 GB**
HDF1 - Ext3, contains multimedia and program setups for Windows.

**Maxtor 80 GB**
HDH1 - Ext3, contains nothing yet.


When I installed Ubuntu after I installed windows, I formatted the leftover space as Ext3.  I then installed ext2fs in Windows, and was able to see and assign letters to the Linux partitions on the boot drive (HDA2, HDA3, HDA4).

I then installed each additional hard drive one at a time in Ubuntu only, as I wanted to get each one right, and have data on two that I didn't want to lose.  It's also easier to backtrack with one at a time if something goes wrong.

**Summary:**
So the three drives that I installed after I installed ext2fs are not accessible.  Ideas?

---

### Post by Tom Brokaw on 2006-08-23
I think I will have to institute a policy of waiting for one day before I post.  That way I will discover the answer to my questions **before** I post them, instead of about 20 seconds after. :redface: 

For anyone else who may have a similar question, in Settings>Control Panel there is an entry called IFS drives; simply select the drive letters you desire and the drives will be accessible from My Computer.

---

