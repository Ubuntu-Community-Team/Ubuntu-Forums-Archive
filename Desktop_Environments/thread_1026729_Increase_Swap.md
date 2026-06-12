---
title: "Increase Swap"
date: 2008-12-31
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2008-12-31
Hello Every one,

Please let me know how to increase my swap memory. Currently it shows 0MB. I wanted to speedup my system by increasing swap memory.

Regards,

Swaroop Kunduru.

---

### Post by taurus on 2008-12-31
Do you mean your swap is not mounted or it is not beening used at all?

Post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by snova on 2008-12-31
> **SwaroopKunduru said:**
> Please let me know how to increase my swap memory. Currently it shows 0MB. I wanted to speedup my system by increasing swap memory.

That only means it isn't being used. That's a *good* thing. ;)

Swap doesn't speed anything up- if your computer ever starts using it, it'll *slow down*.

Swap is merely a chunk of disk space that is used to "extend" your memory when you run out. Accessing the disk is a **lot** slower than accessing memory.

---

