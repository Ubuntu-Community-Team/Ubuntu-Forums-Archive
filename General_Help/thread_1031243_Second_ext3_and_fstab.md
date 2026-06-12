---
title: "Second ext3 and fstab"
date: 2009-01-05
forum: General Help
---

### Post by linuxad on 2009-01-05
I have two hdd partition on my computer. Second partition is mounting but I can't cut file or folder. Its fstab entry :

```
# /dev/sda5
UUID=fe4a2728-a53c-46a6-9a70-0ea499bb8dae /media/depo     ext3    relatime        0       2
```

How can i fix it?

---

### Post by linuxad on 2009-01-05
I changed it:
```
# /dev/sda5
UUID=fe4a2728-a53c-46a6-9a70-0ea499bb8dae /media/depo     ext3    auto,users,rw,exec     0       2
```
But it is useless. I dont use windows now. Please help me!

---

