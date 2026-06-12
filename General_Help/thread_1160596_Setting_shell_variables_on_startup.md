---
title: "Setting shell variables on startup"
date: 2009-05-15
forum: General Help
---

### Post by tenmilez on 2009-05-15
Where should I put variable declarations so that they load on startup and not necessarily when a particular user logs in?

Thanks.

---

### Post by x22 on 2009-05-15
/etc/profile is the usual place: here's
some of mine:

export EDITOR=zile
export GPSPORT=/dev/ttyS0
export INITRD_OK=1
export PATH
export MANPATH=/usr/share/man:/usr/X11R6/man:

---

