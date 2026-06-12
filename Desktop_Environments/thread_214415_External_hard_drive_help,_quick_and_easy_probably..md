---
title: "External hard drive help, quick and easy probably.."
date: 2006-07-12
forum: Desktop Environments
---

### Post by FynitE! on 2006-07-12
Hello.

I installed Kubuntu today, and need to access my external hard drive, but it is read only.

What is the konsole command to remove the read only flag?

Thanks for any help, its appreciated ;)

---

### Post by Paerez on 2006-07-12
you have to mount it read/write. Can you post your "/etc/fstab" please?

---

### Post by T700 on 2006-07-12
What file system is the external drive formatted with?  If it is NTFS (Windows), it is read only under Linux.  You could reformat all or part of it to FAT32 so it could be read by both Windows and Linux or to a native Linux format, if you intend to use it only with Ubuntu.

Paul

---

