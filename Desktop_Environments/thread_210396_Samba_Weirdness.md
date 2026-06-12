---
title: "Samba Weirdness"
date: 2006-07-06
forum: Desktop Environments
---

### Post by magii on 2006-07-06
I have 2 samba shares that I'm trying to mount on startup.  If I do a 'sudo mount -a' everything works fine but I can't get this to work automatically on startup.  Why does mount -a work but autostart not?

My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/ntfs     ntfs    ro,nls=utf8,umask=0222  0  0
//familyroom/network  /media/network  smbfs  credentials=/home/craig/.smbpasswd,uid=craig,gid=craig  0  0
//familyroom/shareddocs  /media/shareddocs  smbfs  credentials=/home/craig/.smbpasswd,uid=craig,gid=craig  0  0

---

