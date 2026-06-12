---
title: "Best 3D chess?"
date: 2008-08-16
forum: Gaming &amp; Leisure
---

### Post by lorgonjortle on 2008-08-16
Greetings,

 As a warning, I am a noob to Linux in general. With that said, on to my question:

 I love chess. I want a nice 3D chess game for my Ubuntu (Hardy). I was reading a post earlier on this site about Dreamchess, so I went into Add/Remove and got it. And as one of the posters in that thread said, the graphics really aren't that great. After visiting the website I realized that I had only gotten the V 1.0 when 2.0 is out. So I downloaded the "tarball" (I think that's what it's called) and did this... here is the output: 

```
lorgonjortle@LorgonJortle-laptop:~$ cd Desk*
lorgonjortle@LorgonJortle-laptop:~/Desktop$ tar xfz dream*
lorgonjortle@LorgonJortle-laptop:~/Desktop$ cd dream*
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ ls
aclocal.m4    configure     desktop               install-sh   NEWS
AUTHORS       configure.ac  doc                   m4           pkg
ChangeLog     COPYING       DreamChess.xcodeproj  Makefile.am  README
config.guess  COPYRIGHT     English.lproj         Makefile.in  src
config.h.in   data          Info.plist            man          ylwrap
config.sub    depcomp       INSTALL               missing
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ sudo ./configure
[sudo] password for lorgonjortle: 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for flex... no
checking for lex... no
checking for bison... no
checking for inline... inline
checking for ISO C99 varargs macros... yes
checking for GNU C varargs macros... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.6... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
checking for SDL_image.h... no
checking for SDL_opengl.h... no
checking for sqrt in -lm... yes
checking for compress in -lz... no
checking for png_create_read_struct in -lpng... no
checking for jpeg_CreateCompress in -ljpeg... no
checking for IMG_LoadPNG_RW in -lSDL_image... no
checking for glBegin in -lGL... no
checking for SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking mxml.h usability... no
checking mxml.h presence... no
checking for mxml.h... no
configure: error: Cannot find Mini-XML header file.
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ 

```

What do I need to get to make it work? I see there are quite a few 'no's there... :confused:

Thanks for any help!

---

### Post by ad_267 on 2008-08-16
Have you tried enabling the 3D mode in the default chess game that comes with Ubuntu? Usually you get a message about needing to install some python module though but that's easy enough to find.

I don't know what the "cannot find Mini-XML header file." All I could find in the Ubuntu repos was libxml-mini-perl, which I don't think would be right.

For the sdl part you probably need the libsdl1.2-dev package.

---

### Post by lorgonjortle on 2008-08-16
Yeah, it told me that I need Python openGl support and GTKGLExt suppoort. That made me lost, haha.

---

### Post by ad_267 on 2008-08-16
Ok yeah I couldn't remember what packages you need. You probably need python-opengl and libgtkglext1. Search for them in synaptic to install them.

Install those and see what you think of the 3d chess. I had a look at the dream chess website and it does look a bit nicer than the default chess. Also I found that for the mini xml thing you need to install the libmxml1 and libmxml-dev packages. So if you install those and libsdl1.2-dev you should be able to compile dream chess. Also make sure you have the build-essential package.

---

### Post by lorgonjortle on 2008-08-16
I installed all of those, and my build essential is all set. But I still get the same error. Here is the output:

```
lorgonjortle@LorgonJortle-laptop:~$ cd Desk*
lorgonjortle@LorgonJortle-laptop:~/Desktop$ cd dream*
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for flex... no
checking for lex... no
checking for bison... no
checking for inline... inline
checking for ISO C99 varargs macros... yes
checking for GNU C varargs macros... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.6... yes
checking for SDL_image.h... no
checking for SDL_opengl.h... yes
checking for sqrt in -lm... yes
checking for compress in -lz... no
checking for png_create_read_struct in -lpng... no
checking for jpeg_CreateCompress in -ljpeg... no
checking for IMG_LoadPNG_RW in -lSDL_image... no
checking for glBegin in -lGL... yes
checking for gluUnProject in -lGLU... yes
checking for SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking mxml.h usability... yes
checking mxml.h presence... yes
checking for mxml.h... yes
checking for mxmlLoadFile in -lmxml... no
configure: error: Cannot find Mini-XML library.
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ cd ~
lorgonjortle@LorgonJortle-laptop:~$ clear

lorgonjortle@LorgonJortle-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  xaw3dg
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lorgonjortle@LorgonJortle-laptop:~$ cd Desktop
lorgonjortle@LorgonJortle-laptop:~/Desktop$ cd dream*
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for flex... no
checking for lex... no
checking for bison... no
checking for inline... inline
checking for ISO C99 varargs macros... yes
checking for GNU C varargs macros... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.6... yes
checking for SDL_image.h... no
checking for SDL_opengl.h... yes
checking for sqrt in -lm... yes
checking for compress in -lz... no
checking for png_create_read_struct in -lpng... no
checking for jpeg_CreateCompress in -ljpeg... no
checking for IMG_LoadPNG_RW in -lSDL_image... no
checking for glBegin in -lGL... yes
checking for gluUnProject in -lGLU... yes
checking for SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking mxml.h usability... yes
checking mxml.h presence... yes
checking for mxml.h... yes
checking for mxmlLoadFile in -lmxml... no
configure: error: Cannot find Mini-XML library.
lorgonjortle@LorgonJortle-laptop:~/Desktop/dreamchess-0.2.0$ 

```

There were some more looked-like-realted files in Synaptic.. I'll get them too, haha.

---

### Post by ad_267 on 2008-08-16
Hmm well it got further that time. If you have both libmxml1 and libmxml-dev I would have thought it would be ok though.

---

### Post by lorgonjortle on 2008-08-16
Yeah. The GNU Chess (I think that's what it's called-- the default chess) it works fine, but I was wondering if there were more themes for it... I hve seen screen shots of marble and metal and whatnot.... I only have a crappy-looking wooden one... Know of any?

---

### Post by ad_267 on 2008-08-16
> **lorgonjortle said:**
> Yeah. The GNU Chess (I think that's what it's called-- the default chess) it works fine, but I was wondering if there were more themes for it... I hve seen screen shots of marble and metal and whatnot.... I only have a crappy-looking wooden one... Know of any?

I don't know sorry, I didn't know there were any other themes available for it.

---

### Post by lorgonjortle on 2008-08-16
Oh, alright. Do you know of any... just, like, more appealing ones? I mean, I think Dreamchess would be great if it would work, but it doesn't look like that's going to be happening...

---

### Post by ad_267 on 2008-08-16
It looks like you can get .deb packages for dreamchess from getdeb.net. See [http://www.getdeb.net/app/DreamChess](http://www.getdeb.net/app/DreamChess)

A .deb package is a precompiled binary and is what the package manager uses, you can just double click on it to install. You probably need to install the dreamchess-data package first and then the dreamchess package.

---

### Post by lorgonjortle on 2008-08-16
That did it! You just got a thanks from me!

---

### Post by ad_267 on 2008-08-16
Awesome! Yeah I should have thought to check there earlier.

---

