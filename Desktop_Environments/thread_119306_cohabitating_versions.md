---
title: "cohabitating versions"
date: 2006-01-19
forum: Desktop Environments
---

### Post by bulldogzerofive on 2006-01-19
I recently installed DRI drivers for my on-board video following this thread:

[http://ubuntuforums.org/showthread.php?t=32043](http://ubuntuforums.org/showthread.php?t=32043)

One question:

When i did it, the package complained that it could not find gcc 3.4, so i installed it.  Later i discovered that i already had gcc 4 installed (I don't compile things very often).  They are both currently installed.  Can they cohabitate or did i just ruin something?  If i did ruin something, does anyone know how to fix it?

Thanks,

mh

---

### Post by 23meg on 2006-01-19
It's fine, you can have both. When you want to use 3.4 instead of 4.0, do the following before compiling```
CC=gcc-3.4
export CC
```

---

### Post by bulldogzerofive on 2006-01-19
Cool thank you very much.

---

