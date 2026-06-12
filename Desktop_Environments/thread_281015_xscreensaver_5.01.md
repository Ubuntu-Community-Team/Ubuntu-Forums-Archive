---
title: "xscreensaver 5.01"
date: 2006-10-20
forum: Desktop Environments
---

### Post by nuzzy on 2006-10-20
Has anyone installed xscreensaver 5.01?  They have some pretty cool new themes, but I'm getting an error trying to run "configure".  It's telling me it can't find X libs/headers.

---

### Post by ayoli on 2006-10-20
you may need some dev packages:
```
sudo aptitude install xorg-dev xserver-xorg-dev
```
and maybe more (but i dunno, seek missing files in configure errors and aptitude search packages).

---

### Post by russianpirate on 2006-10-23
If you're looking for new hacks, it's not worth upgrading.
Only new hacks are topblock and glschool since 4.24 and some changes to the api and bugfixes.. don't expect many new hacks.

---

### Post by gschoper on 2006-11-14
> **nuzzy said:**
> Has anyone installed xscreensaver 5.01?  They have some pretty cool new themes, but I'm getting an error trying to run "configure".  It's telling me it can't find X libs/headers.

```
sudo apt-get build-dep xscreensaver
```
will install the required build time dependencies.

BTW, I just built and installed it, and other than a few new hacks, there's no real need to move up to this version from 4.24.

gschoper

---

