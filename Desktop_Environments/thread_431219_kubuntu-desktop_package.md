---
title: "kubuntu-desktop package"
date: 2007-05-02
forum: Desktop Environments
---

### Post by rolandolb on 2007-05-02
I'm running Ubuntu Feisty Fawn 7.04 and installed kubuntu-desktop package in order to have both GNOME and KDE. Everything works fine however, the boot splash screen with the progress bar ( before login window, after grub) shows kubuntu instead of ubuntu. Is there anyway of restoring it back?

---

### Post by k7k0 on 2007-05-03
Try [this]("http://ubuntuforums.org/showpost.php?p=2565139&postcount=2")
Followed by
```
sudo update-initramfs -u
```

---

### Post by rolandolb on 2007-05-04
ok thanks a lot... that worked perfectly!

---

