---
title: "Will not compile Peops plugin/epsxe problem"
date: 2009-04-13
forum: General Help
---

### Post by stukpixel on 2009-04-13
I am using epsxe, and oss is not working, so I opted to find the only plugin that will use alsa, namely the alternate version of peops.

After doing what the guide says it gives me this:

```
gcc -fPIC -c -Wall -mpentium -O3 -ffast-math -fomit-frame-pointer -DUSEALSA  spu.c
cc1: error: unrecognized command line option "-mpentium"
make: *** [spu.o] Error 1

```

Does anyone have the necessary plugin or can someone help me figure out why it will not compile?

I am running ubuntu 8.10 and Epsxe v1.6.0 emulator and using P.E.Op.S. V1.9 source to compile.

---

