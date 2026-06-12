---
title: "Default fstab for cd/dvd drives"
date: 2006-09-21
forum: Desktop Environments
---

### Post by martal on 2006-09-21
Can someone post the default fstab entries for cd and dvd drives?

My fstab lines are:
/dev/hdc /media/cdrw udf iso9660,users,noauto,rw 0 0	
/dev/hdd /media/dvdro udf iso9660,users,noauto,ro 0 0
/dev/hde /media/dvdrw udf iso9660,users,noauto,rw 0 0

These are not working 100%.

---

### Post by Jussi Kukkonen on 2006-09-21
> /dev/hdc /media/cdrw udf iso9660,users,noauto,rw 0 0
That should probably be:
> /dev/hdc /media/cdrw udf,iso9660 users,noauto,rw 0 0
iso9660 is a filesystem (for CD-ROMs), not a mount option.

---

### Post by Omnios on 2006-09-21
There is a good fstab link to tuxfiles in my link that deals with fstab

---

