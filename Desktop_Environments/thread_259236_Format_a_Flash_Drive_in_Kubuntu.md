---
title: "Format a Flash Drive in Kubuntu"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Transport Man on 2006-09-17
How do you format USB flash drives with a different file system in Kubuntu???

---

### Post by bernied on 2006-09-17
You can format with the various mkfs tools. These include mke2fs for ext2 and ext3 and mkfs.vfat (aka mkdosfs) - for FAT16/32. See the man pages for details - eg. 'man mke2fs'. Beware that Windows only likes USB drives to be in FAT (not sure why and not sure whether FAT32 is ok, and maybe ntfs is ok for windows too). If you put one of these sticks into a windows machine, it will tell you it's not formatted and offer to format if for you. If you agree, you will wipe your data.

If you want multiple partitions on the drive, you can do that too, I use fdisk for this.

---

