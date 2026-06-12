---
title: "USB HDD Sharing Help"
date: 2006-09-26
forum: Desktop Environments
---

### Post by kpictjl on 2006-09-26
How do I make my usb hard drive read/writable by all users...or even a group that I specify?  With my logon I am able to r/w fine.

-------------------------------------------------------------------------
bighead@jimsoldgw2k:/media$ ls -l
total 24
lrwxrwxrwx 1 root    root        6 2006-09-17 01:08 cdrom -> cdrom0
drwxr-xr-x 2 root    root     4096 2006-09-17 01:08 cdrom0
drwx------ 2 bighead bighead 16384 2006-09-26 21:56 usbdisk
drwxr-xr-x 2 root    root     4096 2006-09-26 07:41 WD Passport
-------------------------------------------------------------------------

usbdisk is my USB hard drive.  bighead is my userid.
"WD Passport" used to be my USB hard drive before I reformated the HDD from ntfs to fat32 (I want this HDD to also be writeable by windows xp).

Ubuntu Dapper Drake.

Thank you.

---

### Post by ButteBlues on 2006-09-26
Changing "drwx------" to "drwxr-xr-x" ought to do it.

---

### Post by kpictjl on 2006-09-27
how do I do that?  I've drive sudo chmod 777 and 666 but it never changes.  I've tried sudo chown to change the owner and group to root but it does work.  I don't error messages, it just doesn't change the permissions.

---

