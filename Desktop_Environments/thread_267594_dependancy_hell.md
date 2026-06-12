---
title: "dependancy hell"
date: 2006-09-28
forum: Desktop Environments
---

### Post by z987k on 2006-09-28
I can't understand why I keep running into packages that don't have all their deps met when they are on the repositories that came listed with ubuntu.  Right now I'm trying to install xserver-xorg-dev yet libdrm-dev isn't met.  I can go out on the net and find a deb and install it manually, bt then of course it complains about deps not being met, like it didn't even try to find any.

So does anyone know why this is, also any repositories I should add above and beyond the default ones?

Thanks,
Zach

---

### Post by CatKiller on 2006-09-28
libdrm-dev is in the repositories. At least with the Universe and Multiverse ones, since that's what I've got. If you install packages through Synaptic or Aptitude, all the dependencies will be automatically sorted out.

---

### Post by gborzi on 2006-09-28
> **z987k said:**
> 
So does anyone know why this is, also any repositories I should add above and beyond the default ones?


Perhaps it's because you haven't enabled the universe repos. See here to learn how to enable them [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

Regards.

---

### Post by aysiu on 2006-09-28
In Ubuntu, 99% of dependency hell comes from conflicting repositories.

Get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, try again: ```
sudo aptitude update && sudo aptitude install xserver-xorg-dev
```

---

### Post by z987k on 2006-09-29
after getting the new sources list from aysiu's post, it worked out.

Thanks!

---

