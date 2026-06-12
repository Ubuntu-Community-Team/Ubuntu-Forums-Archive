---
title: "mount (rw) ntfs partion"
date: 2006-06-20
forum: Desktop Environments
---

### Post by m.h.shams on 2006-06-20
dear friends.

i want to mount a ntfs partion, with read, write access during startup.

please help me.

---

### Post by aysiu on 2006-06-20
You can't.

Read-only on NTFS.

Change it to FAT32 or Ext3.

---

### Post by ayoli on 2006-06-20
or you have to recompile your kernel with these options:

CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
CONFIG_NTFS_RW=yes

but ntfs write is still experimental, you do that at your own risks

---

### Post by n0yd on 2006-06-20
You could also read up on fuse-ntfs writing, it works for me albeit a bit slow.

n0yd

---

### Post by Blitzace on 2006-06-20
From what I've heard it's still way too experimental, and to actually write anything without corrupting the filesystem the file has to stay the same size (so only modification can be done to files). It's been a while since I gave up looking for a solution and just stuck to FAT32 partitions so there could be better things available. (although I'd expect them to be complicated.)

If you really want to do it you will need to recompile the kernel as someone has said, so look up a guide for that on google.

---

### Post by GoogleNinja on 2006-06-20
there is also a commercial driver written from the ground up by a company called Paragon. havnt used it myself (don't have any ntfs drives), but it looks cool 

[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)

---

