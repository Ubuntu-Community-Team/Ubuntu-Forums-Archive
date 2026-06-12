---
title: "CD/DVD Drive not working with latest stable kernel"
date: 2006-06-12
forum: Desktop Environments
---

### Post by 23meg on 2006-06-12
Upon compiling the 2.6.16.20 kernel from kernel org I lost the ability to mount CDs with the SATA CD drive of my laptop. I get the following error when trying to mount:

```
mount: special device /dev/scd1 does not exist
```

There's nothing resembling a CD drive entry under /dev. Should I make one with mknod? If so, how? Any other ideas?

---

### Post by 23meg on 2006-06-15
I've just compiled a vanilla 2.6.16 with some patches and I have the same problem.

---

