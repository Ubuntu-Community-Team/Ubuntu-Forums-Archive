---
title: "Kubuntu exit options missing"
date: 2007-05-01
forum: Desktop Environments
---

### Post by lugburz on 2007-05-01
Hi, I try to switch my ubuntu to kubuntu installing the kubuntu-desktop package.

All works well but the exit options in KDE simple simply don't exist: tryingto exit while gnome give me 6 options: logout, hibernate, suspend, reboot.... in kde I can only logout. Why this?

---

### Post by k7k0 on 2007-05-01
Try installing the kdm package. If you already installed it try to reconfigure it and select kdm as your default session manager:
```
sudo dpkg-reconfigure kdm
```

In my case was the opposite situation (changing from kubuntu to ubuntu), and i had to change the symlink in /etc/rc2.d/ (pointing /etc/rc2.d/S99kdm to /etc/init.d/kdm and deleting the gdm symlink)

---

