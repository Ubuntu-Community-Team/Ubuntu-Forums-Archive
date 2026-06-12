---
title: "Force mount External Harddrive"
date: 2009-05-08
forum: General Help
---

### Post by jhazard112 on 2009-05-08
My external harddrive was turned off by a power outage and I already had my laptop powered down, but when I came in this morning it will not mount my external.  I need some help and I am a newb, any help would be much appreciated.  I am getting this error "cannot mount volume.   Invalid mount option when attempting to mount the volume."

Hazard

---

### Post by StOoZ on 2009-05-08
pate the output of :
> sudo fdisk -l

---

### Post by jhazard112 on 2009-05-08
> **StOoZ said:**
> pate the output of :
Ok so I went ahead and did that...it is recognizing the drive showing me the breakdown of it, but it is not mounting it still

---

### Post by jhazard112 on 2009-05-08
> **StOoZ said:**
> pate the output of :

just checked another forum and tried this command 
mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
not sure exactly what that does thought i would try it and i got no such file or directory...any good books for a newb to read to understand a little better lol...

---

### Post by jhazard112 on 2009-05-08
> **StOoZ said:**
> pate the output of :
and sorry for not saying this earlier but this is a windows external harddrive i.e. it is in ntfs format

---

