---
title: "libnm-glib-dev broken"
date: 2006-07-12
forum: Desktop Environments
---

### Post by WiLLiE on 2006-07-12
Hi, i'm trying to compile [Tinymail]("https://svn.tinymail.org/svn/tinymail/trunk/") however it bails out.

"No package 'libnm_glib' found"

So I searched and found the package "libnm-glib-dev" but it wont install.

```
libnm-glib-dev: Beror: libdbus-glib-1-dev (>= 0.60) men det kommer inte att installeras
E: Trasiga paket
```
and
```
libdbus-glib-1-dev: Beror: libdbus-glib-1-2 (= 0.60-6ubuntu8) men 0.60-6ubuntu9 skall installeras
                      Beror: libdbus-1-dev (= 0.60-6ubuntu8) men 0.60-6ubuntu9 skall installeras
E: Trasiga paket
```

How do I solve this? ](*,)

---

### Post by WiLLiE on 2006-07-13
I got it to compile by manually extracting the debs and installing them that way.
But it would be nice if the mentioned .deb file above would be fixed.

---

