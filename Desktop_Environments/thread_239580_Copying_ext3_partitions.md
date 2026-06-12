---
title: "Copying ext3 partitions"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Steven_B on 2006-08-19
I need to copy an entire ext3 partition to another partition, also formatted as ext3.  Unfortunately, parted gives me this error:```
No Implementation: This ext2 file system has a rather strange layout!  Parted can't resize this (yet).

```
I tried removing the journals of the partitions, but that didn't help.  I checked both partitions with fsck, and they are clean.
Any ideas?

---

### Post by jordilin on 2006-08-19
If you wanna have an exact copy of a partition I would recommend using Partimage. Aysiu made a tutorial here:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) :biggrin:

---

### Post by Steven_B on 2006-08-19
Is partimage able to make an exact copy of the partition, that I can boot and run off of?  I don't have the extra partitions required to make a backup image and restore it to the new partition, so will creating a backup with no compression work?

---

### Post by jordilin on 2006-08-20
> **Steven_B said:**
> Is partimage able to make an exact copy of the partition, that I can boot and run off of?  I don't have the extra partitions required to make a backup image and restore it to the new partition, so will creating a backup with no compression work?

If you don't have extra space, I don't know if with partimage you can create cds on the fly. I can't help you more, because I don't use partimage at all for my backups. Let's see if anyone else can help you out.

---

### Post by Steven_B on 2006-08-21
I tried
```
sudo tar cf - /mnt/hda5 | (cd /mnt/hda6; tar xf -)
```
but tar says:  "Cannot open: No such file or directory" for all of the files.  Am I doing something wrong?

Trying a different way, will the following work if the destination is **larger** than the source?
```
dd if=/dev/hda5 of=/dev/hda6 bs=64M
```

---

