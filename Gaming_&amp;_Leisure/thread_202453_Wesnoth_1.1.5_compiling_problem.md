---
title: "Wesnoth 1.1.5 compiling problem"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by matoxxx on 2006-06-23
i want to compile latest dev of wesnoth but i get this, any clue what shoul i do ?
[HTML]root@matoxxx-ubuntu:/usr/src/wesnoth-1.1.5# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for sdl-config... /usr/bin/sdl-config
checking for fribidi-config... no
configure: WARNING: *** FRIBIDI not found.
checking for libpng-config... /usr/bin/libpng-config
checking for SDL - version >= 1.2.7... yes
checking for gnome-config... no
checking for kde-config... /usr/bin/kde-config
checking for libtool... no
checking for IMG_Load in -lSDL_image... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for SDLNet_Init in -lSDL_net... yes
checking for freetype-config... /usr/bin/freetype-config
checking for libzipios++... no
configure: WARNING: *** libzipios++ not found - support for ZIP files is disable d
checking for dirent.h that defines DIR... no
checking for sys/ndir.h that defines DIR... no
checking for sys/dir.h that defines DIR... no
checking for ndir.h that defines DIR... no
checking for library containing opendir... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@matoxxx-ubuntu:/usr/src/wesnoth-1.1.5# make
make: *** No targets specified and no makefile found.  Stop.
root@matoxxx-ubuntu:/usr/src/wesnoth-1.1.5# make install
make: *** No rule to make target `install'.  Stop.[/HTML]

i installed these dependencies 

```
aptitude install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libfreetype6-dev
```

---

### Post by Perfect Storm on 2006-06-23
Check: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)

---

### Post by matoxxx on 2006-06-23
[QUOTE=Artificial Intelligence]Check: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)[/QUOTE]


Thanks a lot

---

