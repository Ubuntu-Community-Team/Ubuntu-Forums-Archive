---
title: "Package Held Back"
date: 2005-10-13
forum: Desktop Environments
---

### Post by qalimas on 2005-10-13
```
keith@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libsdl-sge-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I upgraded, but got that after I tried again (it did it the first time too).  If I remember correctly, it's been that way ever since I did the flashing Gaim trick in Hoary, I had to lock a package so it couldn't update and stop Gaim from flashing.  Well, now that GNOME supports the flashing, I'd like to unlock that package, but how?

---

### Post by pear-i on 2005-10-13
try 
```
sudo apt-get install libsdl-sge-dev 
```
that should override the package libsdl-sge-dev that is being kept back

---

