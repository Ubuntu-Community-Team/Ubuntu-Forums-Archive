---
title: "Just installed ubuntu and trying to run ezquake"
date: 2006-06-30
forum: Gaming &amp; Leisure
---

### Post by ruzkie on 2006-06-30
./ezquake-gl.glx: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory
what package do i need?

---

### Post by bestial on 2006-10-15
Try

sudo ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0

---

