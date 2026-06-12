---
title: "kde windows/ make failed"
date: 2005-08-07
forum: Desktop Environments
---

### Post by [pl]ice on 2005-08-07
hi, trying to compile kde window themes, it needs kelibs4 , so i installed it, but it seems that its missing:
/usr/include/kde/kdecoration.h
/usr/include/kde/kdecoration_p.h
/usr/include/kde/kdecoration_plugins_p.h
/usr/include/kde/kdecorationfactory.h

?

got errors on make:
  handler.h:23:25: kdecoration.h: No such file or directory
handler.h:24:32: kdecorationfactory.h: No such file or directory



i found these files on warty, but i don't really want to use them, not to mess it up.
are there any other packages with these?
thanks

---

### Post by Firetech on 2005-08-07
All those files are available in the package "kdebase-dev".
The package "apt-file" can be helpful in this situation.

---

### Post by [pl]ice on 2005-08-07
thanks :)

---

