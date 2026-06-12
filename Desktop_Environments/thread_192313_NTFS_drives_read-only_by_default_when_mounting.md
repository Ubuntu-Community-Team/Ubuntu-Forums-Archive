---
title: "NTFS drives read-only by default when mounting?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by gohan80 on 2006-06-08
I have, all in all, 9 NTFS partitions on different disks in my computer. To my surprise all of them are mounted (in fstab) as "default". I figure it's still note safe to write to NTFS partitions from Linux, so what does default actually means? Are they read-only by default? 

Thanks,
Gohan

---

### Post by Ramses de Norre on 2006-06-08
Yes they are, and I wont change that =)

---

### Post by linuchsan on 2006-06-08
delete them in the fstab file and use ntfsmount instead

---

### Post by Ramses de Norre on 2006-06-08
Be sure to realise that you most likely will corrupt your partition tables if you do that. And that's pretty hard to recover..

---

### Post by linuchsan on 2006-06-08
It depends...if you use the ntfs kernel driver, don''t.

---

