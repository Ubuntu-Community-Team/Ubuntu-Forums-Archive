---
title: "Not seeing NTFS partition"
date: 2008-05-03
forum: Desktop Environments
---

### Post by doriard on 2008-05-03
Gutsy made NTFS partitions available automatically, but in Hardy I can't see it, or how to enable it.  How do I enable NTFS paritions in Gnome and make them automatically available at bootup?

---

### Post by Rocket2DMn on 2008-05-03
Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid
```
If you know which device(s) are the problem ones, please point them out.  Also, let me know if they are internal or external drives.

---

### Post by doriard on 2008-05-04
I tried installing psydm -- it's simple and it seems to work so far.  Thanks for offering help.

---

