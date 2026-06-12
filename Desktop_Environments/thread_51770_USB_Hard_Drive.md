---
title: "USB Hard Drive"
date: 2005-07-25
forum: Desktop Environments
---

### Post by alec on 2005-07-25
Hi,

I have a Maxtor Onetouch usb2 external drive, which my wife uses with her beloved Windows, and I would like to use it for daily backups in Kubuntu. 

It is NTFS.

I can get the drive to mount, read what is on it and copy from it. I cannot write to it, nor move stuff from it. The permissions are set to read/write. 

By the way when I was using Suse 9.3 I could only get it to mount as root.

Any ideas as to how I can make full use of this device?

Cheers.

---

### Post by GeneralZod on 2005-07-25
Linux cannot write to NTFS (or rather, the write support is so primitive and incomplete that you may as well say that it can't write to it).  Microsoft refuse to release any specifications for the file system, and it is incredibly hard to reverse-engineer.  One solution is to use captive-ntfs which requires a Windows installation, but I'm not sure I can recommend it as it is slow and I have no idea how reliable it is.

Unfortunately, the only file system that has mature read-write support under both OS's is FAT32, which again I wouldn't recommend for large drives carrying important data as it is a very poor file system.  There are some efforts to write Windows drivers for some of Linux's filesystems (ext2 and 3, I think), but I can't remember what they're called; sorry about that :/

---

### Post by alec on 2005-07-25
Thanks for the advice. I feel Partitionmagic coming out of its box, and the wife buying herself a new drive...

---

