---
title: "Trying to install Heros Of Allacrost"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-06-12
This is the error i get when I go to compile it per the instructions on UGA:

@DualCore-Feisty:~/Desktop/allacrost-0.2.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether to enable -O3 compiler optimization... yes
checking whether to enable debugging... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether to enable usage of map editor... no
checking for XCreateWindow in -lX11... yes
checking for glGetString in -lGL... yes
checking for gluGetString in -lGLU... yes
checking for png_read_info in -lpng... yes
checking for jpeg_read_raw_data in -ljpeg... yes
checking for SDL_InitSubSystem in -lSDL... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for TTF_Init in -lSDL_ttf... yes
checking for SDLNet_Init in -lSDL_net... no
Could not find the SDL_net library. Check that it is properly installed on your system

---

### Post by Ripfox on 2007-06-12
bump

---

### Post by bukwirm on 2007-06-12
It appears that you need the SDL_net library. Try installing the *libsdl-net1.2-dev* package. Feisty may have a different version in it's repositories.

---

### Post by Ripfox on 2007-06-13
Thanks that worked!

---

### Post by RootsLINUX on 2007-06-14
Yeah I forgot that we have that dependency. Its used for a small function that checks online to see if a new version of the game is available, but we aren't using it yet. Glad you got it to compile. :)


If anyone wants to make an official Ubuntu package for Allacrost, please stop by and let our team know. Our Debian packages aren't playing nice with Ubuntu at the moment because of libc version differences and the fact that we now require the Luabind library.

---

### Post by Ripfox on 2007-06-14
Also had to find a library called luabind...then it worked.

---

