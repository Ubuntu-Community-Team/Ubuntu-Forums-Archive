---
title: "is there anything especial with 8.10 ext3 formating procedure?"
date: 2009-01-05
forum: General Help
---

### Post by cormano on 2009-01-05
Let me explain. Ive been a Ubuntu user for quite a long time, since the dapper drake era. In the meantime ive kept using windows too, since there are some programs that i have no replacement for and VM performance aint good enought(mostly after effects). Well, to the point. I always used the ext2ifs driver for windows to access my ext 3 partitions. But i recently noticed i cant access ext3 partitions formated by the Ubuntu 8.10 installer. Is there any particular difference, parameters or anything, between the current installer and the older ones? Im clueless here, any help will be apreciated.

---

### Post by transporter_ii on 2009-03-07
For what it is worth, I have the same issue. Can anyone recommend a replacement driver that does work?

Thanks

---

### Post by LouNGeR on 2009-03-12
**[EDIT]**

This seems to work :)  --> _[Ext2fsd](http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd)_

**[/EDIT]**



I have the same problem.

This is the software that I have used in the hope to read my Ext3 filesystem:

- _[Ext2IFS](http://www.fs-driver.org)_
- _[Explore2fs](http://www.chrysocome.net/explore2fs)_
- _[DiskInternals Linux Reader](http://www.diskinternals.com/linux-reader/)_

None of them actually work...

Ext2IFS seems to mount my partition, and I can see it in Explorer (as U), yet when I click on it, it tells me it needs to be formatted. After reading _[here](http://www.fs-driver.org/troubleshoot.html)_ for troubleshooting, I ran the "mountdiag" utility, which tells me this:

```
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.
```

So, is this the culprit? Ubuntu formats it with an inode of 256, who knows...

---

