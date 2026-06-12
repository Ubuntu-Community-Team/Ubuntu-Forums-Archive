---
title: "Not able to rename"
date: 2009-03-20
forum: General Help
---

### Post by kushal.7 on 2009-03-20
Hi frnds,
his is my second post regarding this.
pls solve my problem.

i can't rename my drive. I got the following error.

Sorry, could not rename "XYZ" to "ABC": Operation not supported by backend.

I don't want to format my drive. Pls help.

---

### Post by taurus on 2009-03-20
Do you want to change the label of your drive or do you want to change the mount point?

---

### Post by kushal.7 on 2009-03-20
I just want to change the label.

---

### Post by taurus on 2009-03-20
What filesystem is it?

---

### Post by kushal.7 on 2009-03-20
Fat32.

---

### Post by kushal.7 on 2009-03-20
how do i rename it ????

---

### Post by taurus on 2009-03-20
Make sure the drive is not mounted first before you change the volume name.

```
sudo mkfs.vfat -n *new_volume_name* /dev/sdb1
```
If /dev/sdb1 is the device you want to change.

---

### Post by kushal.7 on 2009-03-20
Thanks !!!

---

