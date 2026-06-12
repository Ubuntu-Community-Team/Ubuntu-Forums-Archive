---
title: "&quot;File system check failed&quot; Error message..."
date: 2006-09-30
forum: Desktop Environments
---

### Post by Matodo on 2006-09-30
Hello

Everytime I boot to my Dapper I get this error message

```

* Checking all filesystems...
reiserfs_open: the reiserfs superblock cannot be found on /dev/hda7
Failed to open the filesystem

If the partition table has not been changed, and the partition is valid it really contains a reiserfs partition, then the superblock is corrupted and you need to run this utility with --rebuild-sb

File system check failed. Please repair manually
CONTROL-D will exit from this shell and continue system startup

root@mybox :~#

```

So, I press CONTROL-D (or type "exit") and Ubuntu boots normally.

Useful informations:
Ubuntu is installed in hda6 (the filesystem is ReiserFs)
I've got BackTrack installed in hda7 (the filesystem is ReiserFs)

I would like to fix this problem. Any idea ?

Thanks

---

### Post by dcstar on 2006-10-01
> **Matodo said:**
> Hello

Everytime I boot to my Dapper I get this error message

```

* Checking all filesystems...
reiserfs_open: the reiserfs superblock cannot be found on /dev/hda7
Failed to open the filesystem

If the partition table has not been changed, and the partition is valid it really contains a reiserfs partition, then the superblock is corrupted and you need to run this utility with --rebuild-sb

File system check failed. Please repair manually
CONTROL-D will exit from this shell and continue system startup

root@mybox :~#

```

So, I press CONTROL-D (or type "exit") and Ubuntu boots normally.

Useful informations:
Ubuntu is installed in hda6 (the filesystem is ReiserFs)
I've got BackTrack installed in hda7 (the filesystem is ReiserFs)

I would like to fix this problem. Any idea ?

Thanks

[http://ubuntuforums.org/showthread.php?t=133689](http://ubuntuforums.org/showthread.php?t=133689)

---

### Post by Matodo on 2006-10-01
Still having the same problem
Where Can I find the Boot Log ?

---

### Post by Matodo on 2006-10-02
Up

---

### Post by jefflubecki on 2008-05-28
I'm getting a file system check error as well. Can you help

FSTAB:

# /etc/fstab: static file system information.

#

# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0

# /dev/sda1

UUID=eb7a3639-229a-4b82-bbab-f898302f6f09 / ext2 relatime,errors=remount-ro 0 1

# /dev/sdb1

UUID=18b93a52-916d-4651-9f12-3e29229f3dcd /home ext2 relatime 0 2

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0





Thanks!

---

