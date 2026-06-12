---
title: "sdl video problem when running advancemame"
date: 2007-03-10
forum: Gaming &amp; Leisure
---

### Post by Beanalby on 2007-03-10
I'm trying to run advancemame on a 6.10 Desktop installed on a Dell Inspiron 4100, ATI Radeon Mobility video card.

I configured advancemame without framebuffer support, and I'm having problems getting it to use SDL.

I didn't install the sdl-dev package from synaptic because it wanted to remove ubuntu-desktop and xubuntu-desktop to install it (not sure why).  so I downloaded and installed SDL from source and advancemame built fine.  When I run it, I get:

```
ninji@littlebean:~$ advmame tmnt
AdvanceMAME - Copyright (C) 1999-2003 by Andrea Mazzoleni
MAME - Copyright (C) 1997-2003 by Nicola Salmoria and the MAME Team
Unable to initialize the video driver. The errors are:
sdl: Unable to intialize the SDL library, No I/O port permissions.
ninji@littlebean:~$
```

SDL is definitely installed:

```
ninji@littlebean:~$ sdl-config --version
1.2.11
ninji@littlebean:~$ ls -l /usr/local/lib/libSDL*
lrwxrwxrwx 1 root root      20 2007-03-10 17:52 /usr/local/lib/libSDL-1.2.so.0 -> libSDL-1.2.so.0.11.0
-rwxr-xr-x 1 root root  910862 2007-03-10 17:52 /usr/local/lib/libSDL-1.2.so.0.11.0
-rw-r--r-- 1 root root 1347572 2007-03-10 17:52 /usr/local/lib/libSDL.a
-rwxr-xr-x 1 root root     819 2007-03-10 17:52 /usr/local/lib/libSDL.la
-rw-r--r-- 1 root root    3362 2007-03-10 17:52 /usr/local/lib/libSDLmain.a
lrwxrwxrwx 1 root root      20 2007-03-10 17:52 /usr/local/lib/libSDL.so -> libSDL-1.2.so.0.11.0
ninji@littlebean:~$
```

Don't know where to head from here, any ideas?

---

