---
title: "Help mounting an external hard disk."
date: 2009-05-18
forum: General Help
---

### Post by DanielC on 2009-05-18
Hello.

I have an external USB hard disk which I have formatted with two ext3 partitions. When I plugin the disk, the partitions are mounted but owned by *root*. So I can't access the partitions as a regular user.

Any ideas?

---

### Post by taurus on 2009-05-18
Just change the mount points for those two ext3 partitions from root to your login name.  Then, you can write to them anytime you want.

```
sudo chown -R username:username /media/data
```
Replace username with your login name and use the right mount point.

---

### Post by DanielC on 2009-05-19
Amazingly, that actually worked. I didn't think it woul work, but I tried it and it did (with the slight change that I didn't chown the mount point but rather the parent directory - ie. /media).

Thanks.

---

