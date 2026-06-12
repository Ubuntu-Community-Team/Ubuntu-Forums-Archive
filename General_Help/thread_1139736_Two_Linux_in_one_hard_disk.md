---
title: "Two Linux in one hard disk?"
date: 2009-04-27
forum: General Help
---

### Post by eufran on 2009-04-27
Hello, i have one hard disk with windows xp and ubuntu 9.04.
All works perfect.

But now i have install one distribution of Ubuntu 8.09 and now the grub when i have to go Ubuntu 9.04 show error grub 2.
bad file or directoy


i no have to access to my ubuntu 9.04 where i have all files.

Helpppppppp

---

### Post by mali2297 on 2009-04-27
From Ubuntu 8.09 (sic), open a terminal and type
```

fdisk -l

```
to list the partition table. Post the result. Do you recognize the partition that you want to access? (Go by the size.)

---

