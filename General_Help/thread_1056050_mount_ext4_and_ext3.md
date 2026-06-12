---
title: "mount ext4 and ext3"
date: 2009-01-31
forum: General Help
---

### Post by Woody1987 on 2009-01-31
I have an external hard drive formatted as ext4. Intrepid will not allow me to mount it as it is. Can i mount it as ext3? or convert it back to ext3?

---

### Post by taurus on 2009-01-31
Does intrepid kernel supports ext4?  You can use gparted in System -> Administration (install it if you don't have it on your machine) to reformat it to ext3 or you can do it from a terminal, assuming it's /dev/sdb1.

```
sudo mke2fs -j /dev/sdb1
sudo mount mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

