---
title: "Adding Windows 7 to GRUB"
date: 2009-01-15
forum: General Help
---

### Post by shade11 on 2009-01-15
I recently installed the latest Windows 7 beta to another hard-drive.

During this process I unplugged my other two hard drives containing Ubuntu 8.10 and Windows XP. I allowed the installation disk to take over an entire hard drive.

However, it seems I get a problem when adding Windows 7 to my menu.lst file. Whenever I boot into Windows 7 via grub, I get the error "Bootmgr is missing."

The entry reads as follows:

```
title		Windows 7
root		(hd2,1)
savedefault
map		(hd2) (hd1)
savedefault
makeactive
chainloader +1
```

---

