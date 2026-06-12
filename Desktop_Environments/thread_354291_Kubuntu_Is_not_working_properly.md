---
title: "Kubuntu Is not working properly"
date: 2007-02-05
forum: Desktop Environments
---

### Post by Metaphysical on 2007-02-05
i just installed kubuntu on top of gnome, and it worked fine for a while. Now when i log into kde, the taskbar at the bottom is empty. I tried to uninstall and reinstall, and i get this error and the end of the install attempt:
Errors were encountered while processing:
 libqt4-gui
 libqt4-sql
 speedcrunch
 kubuntu-desktop
 qt4-qtconfig
 python-qt4
 libqt4-qt3support
 hwdb-client-kde

---

### Post by aysiu on 2007-02-06
Have you tried this? ```
sudo dpkg --configure -a
```

---

### Post by Metaphysical on 2007-02-06
> **aysiu said:**
> Have you tried this? ```
sudo dpkg --configure -a
```

when i do that i get the same "errors were encountered while processing" error

---

### Post by aysiu on 2007-02-06
Not exactly a fix, but you may want to check out this thread:
[http://ubuntuforums.org/showthread.php?t=345250](http://ubuntuforums.org/showthread.php?t=345250)

---

