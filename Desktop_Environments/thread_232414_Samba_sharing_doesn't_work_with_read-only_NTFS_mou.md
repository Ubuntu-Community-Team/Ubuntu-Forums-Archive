---
title: "Samba sharing doesn't work with read-only NTFS mount"
date: 2006-08-08
forum: Desktop Environments
---

### Post by jobby on 2006-08-08
Hi, I'm trying to share folders from read-only mounted NTFS shares. My /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       /home           ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdb1       /media/sdb1     ntfs-3g    silent,umask=0,locale=en_US.utf8    0    0
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

If I share folders in sdb1 (NTFS mounted readwrite, thanks to ntfs 3g), I can access them fine. However if I try sharing folders from sda1 or hdc1, the share appears when browsing the machine but it can't be accessed. This happens both with Windows machines and the Ubuntu machine sharing the folders. The precise error in Ubuntu is "The folder contents could not be displayed. "Applications" couldn't be found. Perhaps it has recently been deleted." Can anyone help?

---

### Post by jobby on 2006-08-08
One of these days I'll actually search the forums *properly* before asking a question...hopefully this will be useful to someone with the same problem: 
I changed the two ntfs lines in my /etc/fstab from this:

/dev/hdc1 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

to:

/dev/hdc1 /media/hdc1 ntfs defaults,nls=utf8,umask=022,gid=46 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=022,gid=46 0 1

All works good now :-)

---

