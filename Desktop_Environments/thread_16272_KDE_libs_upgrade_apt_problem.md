---
title: "KDE libs upgrade apt problem"
date: 2005-02-20
forum: Desktop Environments
---

### Post by rosslaird on 2005-02-20
I did my usual update/upgrade this morning, and I got this:

Preparing to replace kdelibs-data 4:3.3.2-1ubuntu6 (using .../kdelibs-data_4%3a3.3.2-1ubuntu7_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.3.2-1ubuntu7_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/applications.menu', which is also in package gnome-menus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.3.2-1ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I suppose I could muck around and rename applications.menu to see if it would fix the problem, but first I wanted to see if anyone has a more elegant solution.

Ross

______________________
Edit, 5 minutes later:

Actually, I got impatient and tried it anyway. It didn't work. I get the same error message after renaming applications.menu. I suppose the problem is really with the package gnome-menus. Suggestions welcome...

---

### Post by felipe on 2005-02-20
renaming the file won't work, read this post:

[http://www.ubuntuforums.org/showthread.php?t=16265](http://www.ubuntuforums.org/showthread.php?t=16265)

---

