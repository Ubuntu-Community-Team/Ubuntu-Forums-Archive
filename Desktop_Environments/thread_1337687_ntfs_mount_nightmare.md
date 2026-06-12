---
title: "ntfs mount nightmare"
date: 2009-11-25
forum: Desktop Environments
---

### Post by pette on 2009-11-25
Hey guys,

I'm having a problem mounting an ntfs drive under intrepid:

# fdisk -l
/dev/sda5           13056       60801   383519713+   7  HPFS/NTFS


fstab:
/dev/sda5	/media/backup	auto	rw,noauto,user,noexec,async,umask=0	0 0


$ ls -ld /media
drwxrwxrwx 1 root root 4096 2009-08-06 21:22 /media/backup/


As a user, after mounting the drive,
When trying to create a folder:	"Operation not permitted"
When trying to create a file:	"You do not permissions to write to destination"

Strangely, the same happens with root!!!

This is driving me insane as I do not understand why!

---

