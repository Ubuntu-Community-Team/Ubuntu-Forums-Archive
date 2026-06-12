---
title: "gnome-app-install broke"
date: 2005-06-08
forum: Desktop Environments
---

### Post by secundar on 2005-06-08
```
$ sudo gnome-app-install
Reading package lists... Done
Building dependency tree... Done
Traceback (most recent call last):
  File "/usr/lib/gnome-app-install/AppInstall.py", line 125, in idle
    self.updateCache()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 144, in updateCache
    self.populate_menu()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 242, in populate_menu
    import locale ; menu.setLocale(locale.getlocale(locale.LC_MESSAGES)[0])
AttributeError: Menu instance has no attribute 'setLocale'
``` 

I've reinstalled it with synaptic but I get the same report when launching gnome-app-install from the terminal. When using the menu I just get a spinning cursor.

---

### Post by Burgundavia on 2005-06-08
Have you reported a bug about this?

bugzilla.ubuntu.com

Corey

---

### Post by Majlo on 2005-06-16
OK the bug is fixed ..
See this page [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

---

### Post by bier444 on 2005-06-30
have a look at message 9 in

[http://www.ubuntuforums.org/showthread.php?t=41839](http://www.ubuntuforums.org/showthread.php?t=41839)

bier444

---

