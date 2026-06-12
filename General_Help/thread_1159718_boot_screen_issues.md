---
title: "boot screen issues"
date: 2009-05-14
forum: General Help
---

### Post by melzanis on 2009-05-14
Okay I have been reading the forums for how to change my boot screen. However, it would seem that after restarting my computer. I just get the -- not sure what to call it-- system startup checks.
e.g.*?[OK]
then it brings me back to my login screen; which I have been able to change much easily.

[http://jayant7k.blogspot.com/2007/06/change-boot-splash-screen-ubuntu.html](http://jayant7k.blogspot.com/2007/06/change-boot-splash-screen-ubuntu.html)

that is just one of the sites I used.
With this site I was able to get the latter half of the sites notes to work. Once I got to
sudo dpkg-reconfigure linux-image-
Package `linux-image-' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image- is not installed

I was also able to get the startup-manager to open, now I can't get it to open.

I have to say that I'm at a lose here!
any help would be great =D

---

### Post by melzanis on 2009-05-15
Bump!!

---

### Post by neo_1in on 2009-05-15
the command should be:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

