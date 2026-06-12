---
title: "Re-partitioning a drive"
date: 2006-08-30
forum: Desktop Environments
---

### Post by mjpatey on 2006-08-30
Hi,

I just did a search on this, but couldn't find what I'm looking for...

Where do you go to re-partition a hard drive?  My main Ubuntu drive (ext3 formatted) currently has 40GB free, and I'd like to allocate 10GB for a vFAT partition to share files with Windows.

In System-> Administration-> Disks, I can view partitions, etc., but there's no facility for creating a new partition in unused space.

I know I've done this before in a previous install, but for the life of me can't remember where!

Thanks for any help you may have.

---

### Post by hopstah on 2006-08-30
```
sudo aptitude install gparted
```  but this is also available on the livecd that you can download and boot to.

---

### Post by asplode on 2006-08-30
Or just pop in the Ubuntu Installation CD, and System->Administration->Gnome Partition Editor

---

### Post by tzulberti on 2006-08-30
> **asplode said:**
> Or just pop in the Ubuntu Installation CD, and System->Administration->Gnome Partition Editor

You could not partition when it is mounted. You should umount, and that is the reason why you should use livecd.

---

### Post by GadgetsGuy on 2006-08-30
if your machine has a dual boot with windows on it, save yourself alot of messing around and use Partition Magic in windows to resize/move your ext3 partitions.

Works like a charm!

:cool:

---

### Post by hopstah on 2006-08-30
> **GadgetsGuy said:**
> if your machine has a dual boot with windows on it, save yourself alot of messing around and use Partition Magic in windows to resize/move your ext3 partitions.

Works like a charm!

:cool:
that is, of course, assuming that one actually owns partition magic.  this is a free way to accomplish the same task.

---

