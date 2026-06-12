---
title: "two disks getting the same name"
date: 2009-06-03
forum: General Help
---

### Post by anonymous_user on 2009-06-03
My externel drive is sdb1 but if I disconnect it and plugin my Corsair Voyager, then it will become sdb1. 

This becomes a problem since I added sdb1 to fstab and the drives use different file systems, and whatnot.

Is there a way to prevent this (other than plugging in both drives concurrently)?

---

### Post by Legace on 2009-06-03
> **anonymous_user said:**
> My externel drive is sdb1 but if I disconnect it and plugin my Corsair Voyager, then it will become sdb1. 

This becomes a problem since I added sdb1 to fstab and the drives use different file systems, and whatnot.

Is there a way to prevent this (other than plugging in both drives concurrently)?

You could plug in both drives, get their UUID (type **blkid** in Terminal) and create seperate entries for both in /etc/fstab based on their UUID.

---

