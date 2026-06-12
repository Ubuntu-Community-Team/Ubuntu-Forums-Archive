---
title: "Nautilus question?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by orb9220 on 2006-07-15
I was coping a folder called Images off my dvd to my media/hdd1/ fat partition.

In tree mode I could not left click drag to hdd1 root.

I had to create a folder on hdd1 called Images then open images folder on dvd and manually left lasso all the folders then left click drag to hdd1/images.

Why can't I drag a folder to root of hdd1?

Thanks

---

### Post by Jagot on 2006-07-15
The only directory you have permission to write to normally is your /home directory.

If you want to copy stuff graphically to another directory then launch Nautlilus using the following command from alt+f2:

```
gksudo nautilus
```

---

### Post by orb9220 on 2006-07-15
I was running a sudo nautilis when I had this issue.

Thanks for responding.

---

### Post by fragos on 2006-07-15
Draging files between partitions acts like a copy instead of a move.  Normally if you can't write its a permissions thing or MS NTFS.  There may be some issues relating to the different on disk format e.g. FAT and EXT3.

---

### Post by orb9220 on 2006-07-15
Thanks for the help just thought it wierd that i can't drag to the root of hdd1.

But can create a folder their than drag files into folder just fine.

---

### Post by aysiu on 2006-07-16
You need to mount the FAT partition properly:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

