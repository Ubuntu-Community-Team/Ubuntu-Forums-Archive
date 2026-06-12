---
title: "Compiling Mupen64Plus - zlib problem"
date: 2011-08-29
forum: Gaming &amp; Leisure
---

### Post by NilPointer on 2011-08-29
I want to compile fresh Mupen64Plus build from latest sources. It requires zlib development libraries. I've installed zlib1g-dev, but still when compiling, i get

Makefile:161: *** No zlib development libraries found!

Any suggestions?

Also, here's link:

[http://code.google.com/p/mupen64plus/wiki/CompilingFromHg]("http://code.google.com/p/mupen64plus/wiki/CompilingFromHg")

---

### Post by NilPointer on 2011-08-30
Seems, that there's no zlib.pc file for pkg-config. How to create one?

---

### Post by NilPointer on 2011-08-30
Problem solved. I've made zlib.pc file myself.

[quote=zlib.pc]prefix=/lib
exec_prefix=${prefix}
libdir=${exec_prefix}
includedir=${prefix}/include

Name: zlib
Description: zlib compression library
Version: 2.0
Cflags: -I${includedir}
Libs: ${libdir}/libz.so.1.2.3.3[/quote]

After that, Mupen64Plus compiled successfully.

---

