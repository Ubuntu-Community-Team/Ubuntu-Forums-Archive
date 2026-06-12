---
title: "Dave Gnukem - sdl issue"
date: 2007-08-30
forum: Gaming &amp; Leisure
---

### Post by fred3000 on 2007-08-30
Hello all.

I'm new to linux, though Ubuntu is not the first distro I've tried. I'm usig Ubuntu 7.04 with the AMD64 architecture.

I'm trying to run Dave Gnukem, which I unzipped somewhere in my home/user directory, but I always get the same error:

./davegnukem: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I know that libSDL as well as libSDL-dev are installed on my system via Synaptic. I've also tried to link the library using:

ln -s /usr/lib/libSDL-1.2.so.0

in the directory where the davegnukem binary is, but it doesn't help at all.

I always get the same error message.

Please help. What am I doing wrong?

---

### Post by cogadh on 2007-08-30
Put the sympbolic link in the same directory that the SDL lib is already located, not in the game's directory. The game should be checking the system environment paths, not your home directory for the library.

---

### Post by fred3000 on 2007-08-30
There is already a symbolic link: /usr/lib/libSDL-1.2.so.0 and the library itself:/usr/lib/libSDL-1.2.so.0.11.0  if that's what You mean. I tried to reinstall the SDL library but it didnt help either.

---

### Post by cogadh on 2007-08-30
Hmmm, do you have version 0.56, downloaded from Sourceforge? I just downloaded that one and tried it, it worked fine. There is a possibility that the problem could have something to do with using the 64-bit version of Ubuntu, but I can't be sure (I'm using 32-bit Ubuntu).

---

### Post by fred3000 on 2007-08-30
Yes, I've downloaded the newest version 0.56. 
Mabe I should try the 32bit version of Ubuntu for more compatibility. I remember having the same problem with the sdl library on Sabayon Linux 64bit.

Thanx for Your help.

---

