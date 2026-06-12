---
title: "libGLU.so.1 not found when trying to run Neverwinter Nights"
date: 2013-11-13
forum: Gaming &amp; Leisure
---

### Post by burdebc on 2013-11-13
Every time I have installed Neverwinter Nights I have had problems with shared libraries not being found.  This time it is libGLU.so.1 that it is looking for.  Previously I would just copy the needed library to the miles folder and rename it to what neverwinter nights was looking for.  When I tried the same trick this time I get the following error.

./nwmain: error while loading shared libraries: libGLU.so.1: wrong ELF class: ELFCLASS64

From searching in the package manager I found that this library was in libglu1-mesa.  I found that the error message above means that neverwinter nights was looking for a 32 bit shared library but it found a 64 bit shared library.  Can anyone help me find either the correct package or the 32 bit versioin of libGLU.so.1 so that I can get this working.  Thanks in advance.

---

### Post by sffvba[e0rt on 2013-11-13
See what happens if you run:

```
sudo apt-get install libglu1-mesa:i386
```

---

### Post by burdebc on 2013-11-16
That seemed to fix the problem.  Thanks.

---

### Post by sffvba[e0rt on 2013-11-16
> **burdebc said:**
> That seemed to fix the problem.  Thanks.

Awesome :) Enjoy the game (oh and you can mark your thread as solved - check out [this thread]("http://ubuntuforums.org/showthread.php?t=2121377") on how to do it if you don't know already)

---

