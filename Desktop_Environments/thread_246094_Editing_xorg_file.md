---
title: "Editing xorg file ?"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-28
Hi

I am going to get a new dell tower from my brother soon and I am going to need to edit the xorg file so my monitor will work it requires 1024 x 768 res to work.  How do i get into xorg.conf for monitor?

Thank You!

---

### Post by aysiu on 2006-08-28
```
sudo dpkg-reconfigure xserver-xorg
``` or ```
sudo nano -B /etc/X11/xorg.conf
```

---

