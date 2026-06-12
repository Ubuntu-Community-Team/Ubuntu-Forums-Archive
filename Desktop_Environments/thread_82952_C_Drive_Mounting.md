---
title: "C Drive Mounting"
date: 2005-10-27
forum: Desktop Environments
---

### Post by haniar on 2005-10-27
Hi,

I am using a Live CD. How can I mount the Windows XP hard disk in read / write mode as I need to delete a file which is preventing XP to reboot.

Thank you

---

### Post by fannymites on 2005-10-27
sudo mount -o rw /dev/hdx /media/xxxx   where "x"'s are your drive and mount point.  I think.

---

### Post by jmeadows111 on 2005-10-27
Something to keep in mind -- Linux support for writing to an NTFS file system (as opposed to Fat32) is not exactly rock solid. Deleting this file from within Linux would be a risky move, if your XP partition is formatted using NTFS.

---

### Post by haniar on 2005-10-27
I am a linux beginner. What should xxxx be if I want to delete a file.

Thank you

---

### Post by matthewv on 2005-10-27
the /dev/hdx should be /dev/hda1 for the first hard drive, first partition; /dev/hdb1 for the second hard drive first partition, /dev/hda2 for first hard drive, second partition; etc... The /media/xxxx should be the name of an empty folder in your /media folder (you may have to create one), e.g. /media/windows. However, to delete a file from your xp hard drive I would use a tool like the ultimate boot disk for windows ([http://www.ubcd4win.com/](http://www.ubcd4win.com/)) if available, which has full ntfs read/write support.

---

