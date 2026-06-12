---
title: "terminal command to backup restore"
date: 2012-01-24
forum: Desktop Environments
---

### Post by samkct on 2012-01-24
Hi;
 
I wish to know  if there a Terminal command to backup the entire filesystem to an external media or n/w drive. and restore the same to a new ubuntu machine without crashing the same. :)
 
Regards
SD

---

### Post by Lars Noodén on 2012-01-24
Probably the most useful tool in that area is [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html).  

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

It's at its best when updating a backup copy because it only transfers the changes not the whole file again and again.

---

### Post by samkct on 2012-01-30
> **samkct said:**
> Hi;
 
I wish to know  if there a Terminal command to backup the entire filesystem to an external media or n/w drive. and restore the same to a new ubuntu machine without crashing the same. :)
 
Regards
SD
Will this help the purpose of entire system backup? rather than the data folder.  My intension is to backup the entire linux partition.

---

### Post by Lars Noodén on 2012-01-30
rsync will do that, just be sure to exclude /dev, /proc and /sys

---

