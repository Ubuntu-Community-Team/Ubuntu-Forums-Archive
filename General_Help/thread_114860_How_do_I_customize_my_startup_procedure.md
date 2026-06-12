---
title: "How do I customize my startup procedure?"
date: 2006-01-09
forum: General Help
---

### Post by bannerboy on 2006-01-09
I'm a linux power-user, and I'm used to Gentoo, I just switched to ubuntu about 3weeks ago, and I'm trying to figure out how to change the startup procedure. how do I tell it to start or not start a daemon of my choice?

---

### Post by Lambert on 2006-01-09
The startup programs are in /etc/init.d and linked to the runlevels in /etc/rc?.d

The command update-rc.d is used to remove and add the links and I would guess you're ok with reading the manpage.

---

### Post by ptmurphy on 2006-01-09
Go to System - Preferences - Sessions

and then choose the "Startup Programs" tab and you can have whatever you want to startup when you log in.

---

### Post by bannerboy on 2006-01-09
thanks, I'm used to rc-update, cause of gentoo, but I could get used to update-rc.d, I'm assuming that there similar.

---

### Post by yanik on 2006-01-09
you can also try sysv-rc-conf

---

### Post by gmcle454 on 2006-05-16
I'm also a long-time gentoo user, thanks for the info.

---

### Post by aysiu on 2006-05-16
The ex-Gentoo users may find this a little too GUI (I'm not sure), but you can also use BUM. ```
sudo apt-get update
sudo apt-get install bum
gksudo bum
```

---

