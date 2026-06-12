---
title: "Second Harddrive"
date: 2005-12-31
forum: General Help
---

### Post by thalg on 2005-12-31
Hello..

I had a second harddrive installed, But  I can't write to it I run Ubuntu 5.10,

I have Format it in ext3 and mount it in /home/thalg/disk2,  Can't change permissions, becurce Im not the owner...

What shall I do ??? Want to copy Musik and Vidz to it..

Tnx...

---

### Post by earobinson on 2005-12-31
are you auto mounting it (post your fstab)? or manualy mounting it (post mount command)?

---

### Post by thalg on 2005-12-31
My fstab 

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/home/thalg/disk2	ext3	user,noauto	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by thalg on 2005-12-31
I fix it whit the chmod comand, but tnx anyway...

---

### Post by earobinson on 2005-12-31
/dev/hdb1 /home/thalg/disk2 ext3 umask=000   0       0

try that

---

