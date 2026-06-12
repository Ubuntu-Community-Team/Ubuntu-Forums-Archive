---
title: "Ms Windows HD"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Raul Fuenzalida on 2005-11-05
Hi!

I have two scsi HD, one with Windows XP installed, and the other with Ubuntu.
I would like to know if there is a way to see and read files of the WindowsXP HD, being on Ubuntu. thanks.

---

### Post by spizkapa on 2005-11-05
If the drive is fat32, yes.

If it's NTFS, no.

Simple heh? Basically, there is no proper ntfs support in the kernel yet (MS don't like releasing specs) so while there are some ways to read from ntfs, you certainly won't be able to write and it will always be a little unsafe.

But, you can turn your windows drive to fat32 and be done with it.

---

### Post by Remmelas on 2005-11-05
ubuntu usually sets this up for you on install, but, the secret is in the mount command.  I don't have scsi hard drives myself, and even if i did, i'm sure my setup would be different.  You need to 'mount' your windows partitions onto your ubuntu file system.  I usually create the directory /mnt/windows 
then you can mount the windows file system with ```
mount /path/to/your/windows/partition /mnt/windows
```
for non-scsi users, windows on the first hard drive, first partition the command would look like ```
mount /dev/hda1 /mnt/windows
``` for scsi users it would look more like ```
mount /dev/sda1 /mnt/windows
```.  You would need to replace the /dev/* with whatever device info applies to your windows partition.

---

