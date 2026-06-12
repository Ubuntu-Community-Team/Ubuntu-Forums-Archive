---
title: "vncserver/vncpasswd error"
date: 2006-08-10
forum: Desktop Environments
---

### Post by BakCompat on 2006-08-10
Ok, have 2 6.06 boxes up and running. One of them has vncserver running properly and i can connect to it via SSH or VNC no problem. The other, i can connect via SSH, but *not* VNC. When i log into it and try to get vnc up and running, here's what i get..

vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Hmm.. where to look now?

---

### Post by mlind on 2006-08-10
libstdc++-libc6.2-2.so.3 file is provided by **libstdc++2.10-glibc2.2** package. Try installing that package on the box where the error happens.

---

