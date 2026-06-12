---
title: "Error when making ZSNES?"
date: 2011-08-21
forum: Gaming &amp; Leisure
---

### Post by Livin4Jesus on 2011-08-21
When I try to use the "make" command to build ZSNES (1.51), I get this error:
> **Terminal]
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DNO_PNG -D__OPENGL__ -march=i586 -O3 -fomit-frame-pointer -fprefetch-loop-arrays -fforce-addr -s -D__RELEASE__ -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
tools/strutil.cpp:1: warning: -fprefetch-loop-arrays not supported for this target (try -march switches)
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function &#8216 said:**
>  Error 1

I've installed all of the tools needed, and checked for updates on tools I already had.

---

