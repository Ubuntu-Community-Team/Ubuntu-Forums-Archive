---
title: "Irukandji on laptop with Optimus: libGL.so.1: wrong ELF class: ELFCLASS64"
date: 2011-11-19
forum: Gaming &amp; Leisure
---

### Post by jarl-haggerty on 2011-11-19
I wanted to try out the games in the app store so I bought Irukandji.  I was able to run Irukandji on another laptop, 64 bit Ubuntu 11.04, but now when I run it I get this error.

```
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
/opt/irukandji/Irukandji: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64
```This laptop is 64 bit Ubuntu 11.10 and it has optimus graphics so I run it with ironhide,

```
optirun /opt/irukandji/Irukandji
```If I don't the problem is slightly different

```
/opt/irukandji/Irukandji: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

### Post by Epinephrin3 on 2011-11-21
Try forcing the game to think its on a 32bit OS.

For example in terminal type: linux32 firefox

---

