---
title: "Problem compiling maelstrom"
date: 2006-06-10
forum: Desktop Environments
---

### Post by B_Stil on 2006-06-10
I love this game and I really want to compile the source code so I can play it on my Ubuntu installation.  I have my Nvidia drivers installed and working so everything is ready.  The only problem is when I run the ./configure on the code, here is my output:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking whether make sets ${MAKE}... (cached) yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
```

It's quite obvious that I need to install SDL.  How do I do this?  I try to install the debian package and it says I already have a newer version installed.  Also, I don't know if this is related, but I get this when I try to run make anyway (I realize it won't work):
```
make: *** No targets specified and no makefile found.  Stop.

```

Is this a separate issue or will it work after the code correctly configures?

---

### Post by B_Stil on 2006-06-10
Ok, i figured it out.  Turns out i needed to compile and install SDL and SDL_Net, which worked just fine.  The install of Maelstrom then worked.  Now the problem I'm having is the resolution not being compatible with my monitor.  Is there a way to get it to run in a window?

---

### Post by B_Stil on 2006-06-10
Never mind.  I found the .deb package for it.  Turns out it wasn't the game I was thinking of.

---

