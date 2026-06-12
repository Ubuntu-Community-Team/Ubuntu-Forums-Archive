---
title: "Cannot mount volume - not privileged"
date: 2007-08-16
forum: Desktop Environments
---

### Post by siggijons on 2007-08-16
Whenever i insert a cd the automounter tells me:

Cannot mount volume.
You are not privileged to mount the volume 'XenServer-3.2.0 Linux Pack'.

I have to manually mount it as root. This is ubuntu 7.04,  fully patched.

My fstab is a as follows:
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=f3741df4-1b46-41b9-85b7-cdb46c2d1c59 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=14a614ef-4b93-45ba-b31b-2244814b7d06 /boot           ext3    defaults        0       2
# /dev/sda1
UUID=571D76E170702020 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=baba401b-a7c9-4e4c-930b-e85617155c8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

