---
title: "Mounting Wiindows partitian"
date: 2006-02-06
forum: Desktop Environments
---

### Post by tension on 2006-02-06
I have a question concerning mounting window partitians in Ubuntu.
I ran the <sudo fdisk -l> and located my NTFS partitian on hda1. fine.

When I ran <sudo nano /etc/fstab> for editing I received:

```
# /etc/fstab: static file system information. # # <file system> <mount point> <type> <options> <dump> <pass> proc /proc proc defaults 0 0 /dev/hdb1 / ext3 defaults,errors=remount-ro 0 1 /dev/hdb5 none swap sw 0 0 /dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0 /dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0 /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```


There's no listing for the hda1 partitian to edit. I looked in the /media directory and no files for the hda1 show.
Is this a hidden file, or is some amiss?

e

---

### Post by RAOF on 2006-02-06
If there is no existing entry, just add a new line rather than modifying the existing one.  Additionally, you'll need to make a directory to mount it.  ```
sudo mkdir /media/hda1
```should be sufficient to do that.

---

### Post by tension on 2006-02-06
It worked, Very cool!  Thanks, again

e

---

