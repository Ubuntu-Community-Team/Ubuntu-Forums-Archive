---
title: "Subpixel smoothing don't work"
date: 2009-04-17
forum: General Help
---

### Post by LesterZX on 2009-04-17
Please help, I have upgrade my ubuntu 9.04 - and now cannot turn on subpixel rendering in Gnome.

[ATTACH]110134[/ATTACH]

The only one appliction that still use subpixel rendering is NetBeans, all another applications now use greyscale. "sudo dpkg-reconfigure fontconfig" don't help, all soft is fully updated to latest versions.

P.S. sorry for my bad english

---

### Post by coffeecat on 2009-04-17
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1109871](http://ubuntuforums.org/showthread.php?t=1109871)

There might be some useful information there - particularly post #7. There are several posts that talk about creating symlinks from /etc/fonts/conf.avail to /etc/fonts/conf.d, so see if anything in conf.avail is what you need.

---

### Post by LesterZX on 2009-04-18
> **coffeecat said:**
> Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1109871](http://ubuntuforums.org/showthread.php?t=1109871)

There might be some useful information there - particularly post #7. There are several posts that talk about creating symlinks from /etc/fonts/conf.avail to /etc/fonts/conf.d, so see if anything in conf.avail is what you need.

Big thanks for replay, but this don't help :(

---

