---
title: "permission of external drive"
date: 2009-05-04
forum: General Help
---

### Post by superalanliu on 2009-05-04
Current owner is root, and I can't write to it.

I do gksu nautilus and I can write to it, but I can't change the permissions via the properties in nautilus. So my question is, how do I change the permissions so that my regular user can write to it, without using gksu.

Thanks!

---

### Post by taurus on 2009-05-04
What filesystem is that external drive and what is the mount point, where did you mount it?

```
sudo fdisk -l
df -h
id
```

---

### Post by Locutus_of_Borg on 2009-05-04
sudo chmod -R a+rw /drive

---

### Post by superalanliu on 2009-05-04
> **Locutus_of_Borg said:**
> sudo chmod -R a+rw /drive

works! thanks man!

---

