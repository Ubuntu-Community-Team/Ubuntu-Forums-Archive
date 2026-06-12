---
title: "Boot off 2 different hard drives"
date: 2009-03-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gocards300 on 2009-03-14
I have a dell e310 with XP and just added another hard drive to it with ubuntu 8.10 installed on it.  Is there anyway I can boot off both hard drive without going into the bios and disabling the main drive?

---

### Post by ugm6hr on 2009-03-14
Yes.

Edit the /boot/grub/menu.lst to fing the Windows HD.

I'm sure there are a few similar posts in here with examples - else a grub expert will probably be able to tell you exactly what needs to be added.

It might help if you post the output of:
```
sudo fdisk -l
```

---

