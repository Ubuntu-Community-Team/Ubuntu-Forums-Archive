---
title: "Mount Volume - &quot;You are not privileged to mount this volume.&quot;"
date: 2009-06-04
forum: General Help
---

### Post by hmiguel on 2009-06-04
Hi guys...since yesterday i cant acess my hd...when itr to mount volume i get "You are not privileged to mount this volume."

pls help me

gksudo gedit /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0cd63148-3f7d-453c-b35c-cd671013be7b /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=25F892B551CCDD60 /media/disk ntfs-3g auto 0 0
# /dev/sda5
UUID=617c68f4-fdfb-41f7-9ddf-e454e71045d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by oldos2er on 2009-06-04
Which partition are you trying to mount? And have you created a mount point for it?

 Usually you'd run something like 
**sudo mount /dev/something /media/something**

---

