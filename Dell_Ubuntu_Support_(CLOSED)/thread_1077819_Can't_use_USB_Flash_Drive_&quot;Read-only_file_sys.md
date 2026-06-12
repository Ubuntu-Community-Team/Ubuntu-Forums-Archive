---
title: "Can't use USB Flash Drive: &quot;Read-only file system&quot;)"
date: 2009-02-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-02-22
I can't manage the files on my USB flash drive.
It says "Error removing file: Read-only file system"

here are the mount parameters:

```
/dev/sdb1 on /media/VERTE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)
```

The properties windows identifies the FS as msdos
I think it's a FAT16.

I found a post with someone having a similar problem, he said it got fixed doing ```
sudo fsck.msdos -a /dev/sdb1
```
I tried it and it did not solve the problem.
I can waste the data on it, but I can't format it in ext2 because I'll need it to be usable with Windows.

Here's what fdisk says:
```
Disk /dev/sdb: 1039 MB, 1039925248 bytes
32 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x0007eea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     1014785    b  W95 FAT32

```

Can anyone explain to me what's happening and/or help me fix this?

---

### Post by anjilslaire on 2009-02-22
I've had that occur occasionally. In most cases I just remove it, reboot, and reinsert it while logged in. It then gets mounted under my account, not root.

---

