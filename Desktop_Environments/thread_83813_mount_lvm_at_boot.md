---
title: "mount lvm at boot"
date: 2005-10-29
forum: Desktop Environments
---

### Post by cotcot on 2005-10-29
How can I mount a lvm during boot ?
Manually I can do it by  'sudo mount /dev/Ubuntu/root /media/breezy'. 
Is it by adding a line in /etc/fstab ? (if yes, which one ?)
Thank you

Edit :  problem solved : I added '/dev/Ubuntu/root  /media/breezy  ext2  defaults  0  2' to my fstab.

---

