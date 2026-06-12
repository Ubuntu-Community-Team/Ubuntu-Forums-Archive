---
title: "Nautilus naming /media mounts"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Charles Hand on 2006-07-20
I have three mount points in /media:

sda1
ntfs
fat32

Volumes get mounted to these three according to fstab:

/dev/sda3       /media/fat32    vfat    defaults,utf8,umask=007,gid=1000,uid=1000 0       1
/dev/sda2       /media/ntfs     ntfs    defaults,nls=utf8,umask=007,gid=1000,uid=1000 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Nautilus automagically creates three "places" corresponding to these three mounts, and Nautilus calls them:

sda1
ntfs
MC_TYPENUM

What is this MC_TYPENUM, and why does nautilus name the place MC_TYPENUM instead of using the name of the mountpoint, fat32?

-Charlie

---

