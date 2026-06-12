---
title: "80gb only recognized as 31.49gb/32gb"
date: 2009-04-04
forum: General Help
---

### Post by the2020 on 2009-04-04
Hey 
I had this problem in xp and its still occurring. I reformatted the the hd from ntfs to ext3 and I still have this problem. Can anyone help?

---

### Post by lavinog on 2009-04-09
can you post the output of
```

sudo fdisk -l /dev/sda

```
if the 80g isn't your main hd replace sda with sdb, sdc...etc

---

