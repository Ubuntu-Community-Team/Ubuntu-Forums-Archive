---
title: "cyrillic in nautilus"
date: 2005-06-16
forum: Desktop Environments
---

### Post by crash369 on 2005-06-16
i know this has been brought up before, but there has been no answer/solution.

I have 3 CDs worth of stuff with russian filenames.  Nautilus absolutely refuses to render them as anything but ?????????????

any suggestions?

---

### Post by Alexandr on 2005-06-18
/etc/fstab ?

 > /dev/hdb /media/cdrom0 udf,iso9660 ro,user,noauto,**utf8** 0 0

---

### Post by crash369 on 2005-06-19
cool, that works, thank you :)

---

