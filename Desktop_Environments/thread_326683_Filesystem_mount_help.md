---
title: "Filesystem mount help"
date: 2006-12-28
forum: Desktop Environments
---

### Post by saracen on 2006-12-28
I have a hard drive that is formatted as NTFS and I am using ntfs-3g to mount it as read/write.  It's a large drive that contains lots of stuff, some of which I want to share with other people who connect to my computer and some of which I don't.  The problem is that when I mount the filesystem, i can only specify global masks for the directory and file permissions.  I don't have the granularity of allowing certain people access to certain directories and others no access.  Is there a good way to do this?  Can I mount directories within a filesystem with certain parameters in /etc/fstab and other directories with different parameters?

---

### Post by kidders on 2006-12-28
> **saracen said:**
> when I mount the filesystem, i can only specify global masks for the directory and file permissions.This is a side-effect of using a filesystem that doesn't support traditional ownership & permissions, I'm afraid. The kind of behaviour you're looking for is a feature of filesystems such as Ext3, HFS, ReiserFS, JFS, etc., but not NTFS or FAT.

> **saracen said:**
> Can I mount directories within a filesystem with certain parameters in /etc/fstab and other directories with different parameters?No, but you *may* be able to mount the entire filesystem and rebind parts of it to other locations with different options. It's not something I've ever tried to do, but you could give it a shot...

```
mount -o uid=1001 /dev/sda1 /mnt/mount1
mount --bind -o uid=1002 /mnt/mount1/something /mnt/mount2
```

I haven't a clue what would happen, but there's only one way to find out!

---

