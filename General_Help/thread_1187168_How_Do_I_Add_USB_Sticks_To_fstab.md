---
title: "How Do I Add USB Sticks To fstab?"
date: 2009-06-14
forum: General Help
---

### Post by Mark76 on 2009-06-14
Yes, I know I have to edit it. But what do I put on the line? Besides /dev/sdf1

---

### Post by Chrissss on 2009-06-14
First, find out what partitions are on the stick. Plug the stick into your computer and execute

```
sudo blkid
sudo fdisk -l
```

---

### Post by Mark76 on 2009-06-14
Ubuntu isn't registering the presence of the stick.

---

