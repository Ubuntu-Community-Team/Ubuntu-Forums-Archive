---
title: "Is there anyway to acces my ubuntu 8.10 partition from windows?"
date: 2009-03-21
forum: General Help
---

### Post by andrewwg94 on 2009-03-21
i used to be able to do that with 8.04, but i no longer can. has this been fixed yet?

---

### Post by hikaricore on 2009-03-21
Umm.. updating from 8.04 to 8.10 should not have affected your ability to access your Linux partition from another OS.
Do you have the appropriate driver installed in Windows to access ext2/3 partitions?

---

### Post by meierfra. on 2009-03-21
Did you do a fresh install? 8.10 uses the new ext3 file system with 256 bs/inode.  "ext2IFS" ([from fs-driver.org]("http://www.fs-driver.org/")) cannot handle the 256 bs/inode

You can use [ext2fsd ]("http://sourceforge.net/projects/ext2fsd") in place of ext2IFS, but I heard that it is not quite as stable as ext2IFS.  

It might be possible to convert an ext3 with 256 bs/inode to one with 128 bs/inode, but I don't really know anything about that.

Or you could reinstall, but beforehand create an ext3 with 128/inode.

To find out whether  your file system uses 128 or 256 bs/inode use

```
sudo tune2fs -l /dev/sda5 | grep "Inode size"
```
(here /dev/sda5 needs to be replaced by the device name of your ubuntu partition (use "sudo fdisk -lu" to determine the device name)

---

