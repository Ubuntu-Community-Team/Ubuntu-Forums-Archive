---
title: "Win/Ubuntu mutual partition"
date: 2005-12-10
forum: General Help
---

### Post by Thunk on 2005-12-10
Does anyone know of a good way to create a partition that can be access by both Ubuntu and XP after both were installed (dual-boot)?

Can Partition Magic do it?

---

### Post by linbetwin on 2005-12-10
The filesystem must be FAT32. Do you want to create this partition from free space on your HDD, or do you have a partition you want to convert?

---

### Post by Thunk on 2005-12-10
My XP partition is NTFS. Can XP handle the extra partition if it's FAT32? I would create it from free space.

---

### Post by linbetwin on 2005-12-10
Yes, Xp can read and write to FAT32. FAT32 has some limitation in comparison to NTFS. For example you cannot store files bigger than 4 GB on a FAT32 partition. Other than that, it works fine for both Windows XP and any Linux distribution.

---

### Post by Thunk on 2005-12-10
Thanks linbetwin. How can I create such a partition from within Ubuntu?

---

### Post by linbetwin on 2005-12-10
I think you can do it with a program called gparted, but I've never used it so I wouldn't know the procedure. But I'm sure someone else can help.

---

### Post by Adrian on 2005-12-10
[QUOTE=Thunk]Does anyone know of a good way to create a partition that can be access by both Ubuntu and XP after both were installed (dual-boot)?

Can Partition Magic do it?[/QUOTE]

Well, this Windows XP driver lets you use ext2/ext3 partitions:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I'm using it myself and it works very well, both for reading and writing.

---

### Post by Thunk on 2005-12-10
Thanks Adrian, I think that should do it.

With this driver I can access the Ubuntu partition from XP and In Ubuntu I can mount the XP partition, so this is an even better solution than designating (and therefore wasting) free space for it.

Thanks all!

---

