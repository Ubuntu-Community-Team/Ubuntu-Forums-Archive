---
title: "invalid ELF header"
date: 2009-08-06
forum: Desktop Environments
---

### Post by mslinn on 2009-08-06
I'm running Ubuntu 9.04 64bit on an Intel Core 2 Duo.
```
$ pdftk
pdftk: error while loading shared libraries: /usr/lib/libgcj.so.90: invalid ELF header
$ ls -alF /usr/lib/libgcj.so.90
lrwxrwxrwx 1 root root 16 2009-05-09 19:48 /usr/lib/libgcj.so.90 -> libgcj.so.90.0.0
$ file /usr/lib/libgcj.so.90.0.0
/usr/lib/libgcj.so.90.0.0: data
```What should I do?

---

