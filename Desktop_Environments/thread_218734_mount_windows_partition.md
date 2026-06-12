---
title: "mount windows partition"
date: 2006-07-19
forum: Desktop Environments
---

### Post by abhiomkar on 2006-07-19
I installed fuse & ntfs-3g to have a support for read & write ntfs drives.

Edited fstab like this...
/dev/hda1     /media/hda1     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
/dev/hda5     /media/hda5     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
/dev/hdb5     /media/hdb5     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0

& i did ...

sudo modprobe fuse
sudo umount -a
sudo mount -a

then, all drives were disappeared from my desktop, but when i go & check /media folder all drives were mounted to /media/hda1 , /media /hda5 , /media/hdb5 folders . & i hv a read & write permission to them.

my problem is, I want my drives back to my desktop...

---

### Post by JerMe on 2006-07-19
Have you tried rebooting?

---

