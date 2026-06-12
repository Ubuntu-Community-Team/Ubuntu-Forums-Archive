---
title: "Quake 3 Segfaults on Startup"
date: 2005-12-03
forum: Gaming &amp; Leisure
---

### Post by thread on 2005-12-03
Well I've tried a bunch of stuff, but no luck. Since I recently upgraded to AMD64, I've had no problem with quake4, ut2004, and others... but quake 3 refuses to work:

```

...
------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Segmentation fault

```

I've even tried following the [32-Bit Chroot How-To]("http://ubuntuforums.org/showthread.php?t=24575"), installed nvidia-glx on top of that, and got exactly the same result.

I found [this thread]("http://forums.gentoo.org/viewtopic-t-309613.html") from the gentoo forums about probably the same problem (since et uses the same engine as quake3). People are blaming the gentoo emul-packages package which from [what I can gather]("http://dev.gentoo.org/~plasmaroo/devmanual/archs/amd64/") is a collection of 32-bit libraries... which my chroot'd system would be full of! Where is my problem here, because it doesn't seem to be the  64-bit incompatibility.

---

### Post by thread on 2005-12-06
Who knows what the dilly is here, but I just upgraded to the new nvidia drivers:

NVIDIA-Linux-x86_64-1.0-8174-pkg2.run

and quake3 RUNS!!!!!!! wh00t!

---

