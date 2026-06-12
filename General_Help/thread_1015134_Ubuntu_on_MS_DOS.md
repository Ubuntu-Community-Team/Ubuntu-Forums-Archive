---
title: "Ubuntu on MS DOS?"
date: 2008-12-18
forum: General Help
---

### Post by macintosh on 2008-12-18
Sorry for sounding stupid but can you really install Ubuntu on FAT32 formated dive?

---

### Post by lovelyvik293 on 2008-12-18
Yes you can install it on the FAT32.
But use ext2/ext3 for linux installation.

---

### Post by Titan8990 on 2008-12-18
You CAN but you will run in to tons of ownership and permission issues. It is not recommended.


> But use ext2/ext3 for linux installation.

XFS is also good.

---

### Post by macintosh on 2008-12-18
> **Titan8990 said:**
> 
XFS is also good.

what about HFS+? Then I might be able to access it from the Mac OS X partition of my HD!

---

### Post by cariboo on 2008-12-18
Linux uses it's own file systems, ext3, reiserfs, xfs,jfs and more, but it will read natively most file systems that you can think of. You can use Appletalk to connect to other Apple computers, as well as samba and nfs to access OSX.

Jim

---

