---
title: "Compiling OpenCascade on 64-bit (K)Ubuntu"
date: 2008-03-25
forum: Education &amp; Science
---

### Post by ze_otter on 2008-03-25
Has anyone successfully built OpenCascade on 64-bit Ubuntu/Kubuntu? The instructions for 64-bit compile are rather sparse; I have put the recommended "CXXFLAGS="$CXXFLAGS -ffriend-injection -fpermissive -m64 -D_OCC64" line to ./configure file, put it still fails with this message when building the TKOpenGl module:

```

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[3]: *** [libTKOpenGl.la] Error 1

```

What am I missing here? Does me having an ATI graphics card have something to do with this (OpenGL issue?)? I've searched through both the OpenCascade forums and Google, but no one else seems to have encountered this.

---

### Post by kleeman on 2008-03-26
Try installing xorg-driver-fglrx-dev

---

### Post by ze_otter on 2008-03-27
Installing xorg-driver-fglrx-dev didn't help. After looking at the issue a bit more deeply, I realized the linker was trying to link to libGL.a, which doesn't exist on my system (and is provided by obsoleted libraries anyway). I tried linking it directly to libGL.so.1 and at least the compile went ok; I've yet to try it out and see if it works at all.

---

### Post by Spectre5 on 2009-03-28
> **ze_otter said:**
> Installing xorg-driver-fglrx-dev didn't help. After looking at the issue a bit more deeply, I realized the linker was trying to link to libGL.a, which doesn't exist on my system (and is provided by obsoleted libraries anyway). I tried linking it directly to libGL.so.1 and at least the compile went ok; I've yet to try it out and see if it works at all.

I know this a (almost exactly) a year later...but maybe you are subscribed to this thread...did this work?

---

### Post by Spectre5 on 2009-03-28
<Subscribed to thread>

---

