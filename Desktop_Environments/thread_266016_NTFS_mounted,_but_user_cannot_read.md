---
title: "NTFS mounted, but user cannot read?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-09-26
When I click my desktop (KDE) icon for my NTFS drive, it mounts, but then KDE reports:
```
Could not enter folder /windows.
```

Here's my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1	/windows	ntfs	user,rw		0	0
```

Can't think what the problem could be! Any ideas?

Thanks,
Jarlath

---

### Post by divague on 2006-09-26
Try creating a folder in /media

cd /media
sudo mkdir windows

and in the fstab change this line

/dev/sda1	/windows	ntfs	user,rw		0	0

for this one

/dev/sda1    /media/windows    ntfs  nls=utf8,umask=0222 0    0

---

### Post by QwUo173Hy on 2006-10-02
Thanks divague - that worked!

---

