---
title: "external drive's uuid"
date: 2009-04-29
forum: General Help
---

### Post by chriskin on 2009-04-29
how to i find the uuid of a drive , in order to put it on fstab?

---

### Post by unutbu on 2009-04-29
```
sudo blkid -c /dev/null
```

blkid is the basic command you need. Using "-c /dev/null" tells blkid to rescan your system, which may be necessary if you edited any partitions.

---

### Post by chriskin on 2009-04-29
> **unutbu said:**
> ```
sudo blkid -c /dev/null
```blkid is the basic command you need. Using "-c /dev/null" tells blkid to rescan your system, which may be necessary if you edited any partitions.


thanks it works :)

---

