---
title: "changing splash screen after gdm"
date: 2007-01-30
forum: Desktop Environments
---

### Post by Absurd on 2007-01-30
In my latest thread concerning customization, I have a question about the splash screen that appears after logging in.

How do I change it?

---

### Post by yabbadabbadont on 2007-01-30
```
/home/bubba $ ls -l /usr/share/pixmaps/splash/
total 136
-rw-r--r-- 1 root root 24375 2007-01-27 19:55 blubuntu_splash.png
-rw-r--r-- 1 root root 35324 2006-08-02 09:00 gnome-splash.png
-rw-r--r-- 1 root root 71403 2006-05-30 03:48 ubuntu-slick.png
lrwxrwxrwx 1 root root    19 2007-01-27 20:02 ubuntu-splash.png -> blubuntu_splash.png
```
Add your new splash image to that directory and change the ubuntu-splash.png symbolic link so that it points to it.

---

### Post by Absurd on 2007-01-30
Thanks

---

