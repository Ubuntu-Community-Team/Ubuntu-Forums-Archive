---
title: "Cannot get Battle for Wesnoth to work!"
date: 2007-10-30
forum: Gaming &amp; Leisure
---

### Post by ohmycar on 2007-10-30
Ok so before I made this thread I made sure it was not already solved and even the boards I did find did not offer a solution for me.

Here is my problem:

I downloaded the source for battle for wesnoth (wesnoth-1.2.7.tar.bz2)

Now I went ahead and I downloaded the latest SDL, and installed it.

I do these commands to being installing/compiling the game:

tar xvjf /home/ash/Desktop/wesnoth-1.2.7.tar.bz2
cd wesnoth-1.2.7
./configure

now on this part, it all goes well but at the very end it says:
checking for OGG support in SDL_mixer... no
configure: error: *** SDL_mixer has no OGG support! You need SDL_mixer with OGG support

I can not seem to get this to work. I even tried to install the SDL_mixer with the line ./configure --enable-ogg and still no luck.

anyone might have a possible solution?
if more info is needed , let me know. 

Thanks,
Ash

---

### Post by Vixis on 2007-10-30
you need libogg-dev and libsdl-mixer1.2-dev packages

```
sudo apt-get install libogg-dev libsdl-mixer1.2-dev
```

---

### Post by ohmycar on 2007-10-30
well I did that and I got this:

```

ash@ash-desktop:~$ sudo apt-get install libogg-dev libsdl-mixer1.2-dev
[sudo] password for ash:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libogg-dev is already the newest version.
libogg-dev set to manual installed.
libsdl-mixer1.2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


```

---

### Post by erginemr on 2007-10-30
If you don't mind using a precompiled package, you may give a try to the Wesnoth Debian packages (ver.1.2.6 for Feisty) available in:
[http://www.getdeb.net/app.php?name=The+Battle+for+Wesnoth](http://www.getdeb.net/app.php?name=The+Battle+for+Wesnoth)

I remember having installed and run Wenoth succesfully this way once in the past.

---

### Post by s_spiff on 2007-10-30
Umm, if you can remove those latest SDL Packages you downloaded from the web, and install the ones in the repos. 
Enter this command :

```
[SIZE=2][FONT=Courier New][SIZE=2]sudo apt-get install libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libxxf86dga-dev xorg-dev subversion[/SIZE][/FONT][/SIZE]

```
I used SVN to get the latest, so do this :
[SIZE=2][FONT=Courier New][SIZE=2]svn co svn://svn.icculus.org/alienarena/trunk/ alienarena2007

cd to the cource folder in the alienarena2007 and enter :
```

make install

```

The issue with this is that it doesn't leave you with a handle to start the game from menus or so. 
Hence you create a new document :

```

gedit alienarena2007

```
[/SIZE][/FONT][/SIZE]
enter the following and save :
```

[SIZE=2][FONT=Courier New][SIZE=2]cd ~/alienarena2007 && ./crx.sdl[/SIZE][/FONT][/SIZE]

```
Just make it executable via right click > Permissions > allow to run 

and Then you Edit the menu, and int he games section, add a new item.

Hopefully this will help.

---

### Post by ohmycar on 2007-10-30
I tried removing the SDL's I had and got the ones from the rep. , but still no luck. 

As for getting the svn , you posted one for alienarena... ?

I am going to try to get the 1.2.6 , is there any big difference between 1.2.6 and 1.2.7

---

### Post by ohmycar on 2007-10-30
It seemed the 1.2.6 would not install properly either. I installed this game on my windows partition and I really liked it so I want to get it to work for linux :(

---

### Post by erginemr on 2007-10-31
> **ohmycar said:**
> It seemed the 1.2.6 would not install properly either. I installed this game on my windows partition and I really liked it so I want to get it to work for linux :(

Did you try the precompiled Debian packages in getdeb.net?

---

### Post by DirtDawg on 2007-10-31
> **erginemr said:**
> Did you try the precompiled Debian packages in getdeb.net?

Or better yet:
```
sudo apt-get install wesnoth
```


There's a changelog [here]("http://svn.gna.org/viewcvs/*checkout*/wesnoth/trunk/players_changelog") about 1/3 way down the page. I would guess the changes between the two versions are not a huge deal.

---

### Post by ohmycar on 2007-10-31
Ah thank you, that helped a lot. Much appreciated :)

---

### Post by ohmycar on 2007-10-31
Ok I installed it using

sudo apt-get install wesnoth

and it installed and everything

now I go to games and click on it, but nothing happens, does not respond or anything, nothing shows up and no signs of it even trying to run come up..

was there anything else I was supposed to do?

---

### Post by desertboy on 2007-10-31
Not a lot of help I know but it installed and plays fine from applications add/remove programs in gutsy.

Maybe try removing all related packages in synaptic and install through the add/remove programs.

---

### Post by DirtDawg on 2007-10-31
> **desertboy said:**
> Not a lot of help I know but it installed and plays fine from applications add/remove programs in gutsy.

Maybe try removing all related packages in synaptic and install through the add/remove programs.

Yes. Open Synaptic and choose the "completely remove" option for wesnoth  and then reinstall.

If that does not work, try starting Wesnoth in a terminal (with the command 'wesnoth') and if you get an error message, post the whole thing here. It will contain information that will help us help you.

---

### Post by ohmycar on 2007-10-31
```
ash@ash-desktop:~$ wesnoth
Battle for Wesnoth v1.2.6
Started on Wed Oct 31 18:15:16 2007

started game: 4173775318
error display: Could not initialize SDL: No available video device
Could not initialize video. Exiting.

```

that is what I am getting, but I have the latest SDL installed...

---

### Post by ohmycar on 2007-10-31
this is what I did to install SDL and still no luck

```

ash@ash-desktop:~$ cd SDL-1.2.12
ash@ash-desktop:~/SDL-1.2.12$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether byte ordering is bigendian... no
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking for windres... no
checking for linux-gnu-windres... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working volatile... yes
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for size_t... yes
checking for int64_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for working memcmp... yes
checking for working strtod... yes
checking for malloc... yes
checking for calloc... yes
checking for realloc... yes
checking for free... yes
checking for getenv... yes
checking for putenv... yes
checking for unsetenv... yes
checking for qsort... yes
checking for abs... yes
checking for bcopy... yes
checking for memset... yes
checking for memcpy... yes
checking for memmove... yes
checking for strlen... yes
checking for strlcpy... no
checking for strlcat... no
checking for strdup... yes
checking for _strrev... no
checking for _strupr... no
checking for _strlwr... no
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking for itoa... no
checking for _ltoa... no
checking for _uitoa... no
checking for _ultoa... no
checking for strtol... yes
checking for strtoul... yes
checking for _i64toa... no
checking for _ui64toa... no
checking for strtoll... yes
checking for strtoull... yes
checking for atoi... yes
checking for atof... yes
checking for strcmp... yes
checking for strncmp... yes
checking for _stricmp... no
checking for strcasecmp... yes
checking for _strnicmp... no
checking for strncasecmp... yes
checking for sscanf... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for iconv... yes
checking for sigaction... yes
checking for setjmp... yes
checking for nanosleep... yes
checking for libiconv_open in -liconv... no
checking for pow in -lm... yes
checking for GCC -fvisibility=hidden option... yes
checking for dlopen... yes
checking for dlopen in -lc... no
checking for dlopen in -ldl... yes
checking for dlvsym in -ldl... yes
checking for yasm... no
checking to see if  supports unquoted-sections... no
checking for nasm... no
checking altivec.h usability... no
checking altivec.h presence... no
checking for altivec.h... no
checking for Altivec with GCC -maltivec option... no
checking for Altivec with GCC -faltivec option... no
checking for OSS audio support... yes
checking for dmedia audio support... no
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... not present.
checking for snd_ctl_open in -lasound... no
checking for artsc-config... no
checking for esd-config... no
checking for ESD - version >= 0.2.8... no
*** The esd-config script installed by ESD could not be found
*** If ESD was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESD_CONFIG environment variable to the
*** full path to esd-config.
checking for pkg-config... /usr/bin/pkg-config
checking for PulseAudio 0.9 support... no
checking audio/audiolib.h usability... no
checking audio/audiolib.h presence... no
checking for audio/audiolib.h... no
checking for AuOpenServer in -laudio... no
checking nas/audiolib.h usability... no
checking nas/audiolib.h presence... no
checking for nas/audiolib.h... no
checking for AuOpenServer in -lnas... no
checking for NAS audio support... no
checking for X... no
checking for framebuffer console support... yes
checking for getpagesize... yes
checking for directfb-config... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for DirectFB 0.9.15 support... no
checking for PlayStation 2 GS support... no
checking for SVGAlib (1.4.0+) support... no
checking for libVGL support... no
checking for wscons support... no
checking for OpenGL (GLX) support... yes
checking for Linux 2.4 unified input interface... yes
checking for Touchscreen library support... no
checking for hid_init in -lusbhid... no
checking usb.h usability... no
checking usb.h presence... no
checking for usb.h... no
checking libusb.h usability... no
checking libusb.h presence... no
checking for libusb.h... no
checking for hid_init in -lusb... no
checking for usbhid... no
checking for pthreads... yes
checking for recursive mutexes... yes
checking for pthread semaphores... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating sdl-config
config.status: creating SDL.spec
config.status: creating SDL.qpg
config.status: creating sdl.pc
config.status: creating include/SDL_config.h
config.status: include/SDL_config.h is unchanged
config.status: executing default commands
Generating dependencies for ./src/SDL.c
Generating dependencies for ./src/SDL_error.c
Generating dependencies for ./src/SDL_fatal.c
Generating dependencies for ./src/audio/SDL_audio.c
Generating dependencies for ./src/audio/SDL_audiocvt.c
Generating dependencies for ./src/audio/SDL_audiodev.c
Generating dependencies for ./src/audio/SDL_mixer.c
Generating dependencies for ./src/audio/SDL_mixer_MMX.c
Generating dependencies for ./src/audio/SDL_mixer_MMX_VC.c
Generating dependencies for ./src/audio/SDL_mixer_m68k.c
Generating dependencies for ./src/audio/SDL_wave.c
Generating dependencies for ./src/cdrom/SDL_cdrom.c
Generating dependencies for ./src/cpuinfo/SDL_cpuinfo.c
Generating dependencies for ./src/events/SDL_active.c
Generating dependencies for ./src/events/SDL_events.c
Generating dependencies for ./src/events/SDL_expose.c
Generating dependencies for ./src/events/SDL_keyboard.c
Generating dependencies for ./src/events/SDL_mouse.c
Generating dependencies for ./src/events/SDL_quit.c
Generating dependencies for ./src/events/SDL_resize.c
Generating dependencies for ./src/file/SDL_rwops.c
Generating dependencies for ./src/stdlib/SDL_getenv.c
Generating dependencies for ./src/stdlib/SDL_iconv.c
Generating dependencies for ./src/stdlib/SDL_malloc.c
Generating dependencies for ./src/stdlib/SDL_qsort.c
Generating dependencies for ./src/stdlib/SDL_stdlib.c
Generating dependencies for ./src/stdlib/SDL_string.c
Generating dependencies for ./src/thread/SDL_thread.c
Generating dependencies for ./src/timer/SDL_timer.c
Generating dependencies for ./src/video/SDL_RLEaccel.c
Generating dependencies for ./src/video/SDL_blit.c
Generating dependencies for ./src/video/SDL_blit_0.c
Generating dependencies for ./src/video/SDL_blit_1.c
Generating dependencies for ./src/video/SDL_blit_A.c
Generating dependencies for ./src/video/SDL_blit_N.c
Generating dependencies for ./src/video/SDL_bmp.c
Generating dependencies for ./src/video/SDL_cursor.c
Generating dependencies for ./src/video/SDL_gamma.c
Generating dependencies for ./src/video/SDL_pixels.c
Generating dependencies for ./src/video/SDL_stretch.c
Generating dependencies for ./src/video/SDL_surface.c
Generating dependencies for ./src/video/SDL_video.c
Generating dependencies for ./src/video/SDL_yuv.c
Generating dependencies for ./src/video/SDL_yuv_mmx.c
Generating dependencies for ./src/video/SDL_yuv_sw.c
Generating dependencies for ./src/joystick/SDL_joystick.c
Generating dependencies for ./src/video/dummy/SDL_nullevents.c
Generating dependencies for ./src/video/dummy/SDL_nullmouse.c
Generating dependencies for ./src/video/dummy/SDL_nullvideo.c
Generating dependencies for ./src/audio/disk/SDL_diskaudio.c
Generating dependencies for ./src/audio/dummy/SDL_dummyaudio.c
Generating dependencies for ./src/loadso/dlopen/SDL_sysloadso.c
Generating dependencies for ./src/audio/dsp/SDL_dspaudio.c
Generating dependencies for ./src/audio/dma/SDL_dmaaudio.c
Generating dependencies for ./src/video/fbcon/SDL_fb3dfx.c
Generating dependencies for ./src/video/fbcon/SDL_fbelo.c
Generating dependencies for ./src/video/fbcon/SDL_fbevents.c
Generating dependencies for ./src/video/fbcon/SDL_fbmatrox.c
Generating dependencies for ./src/video/fbcon/SDL_fbmouse.c
Generating dependencies for ./src/video/fbcon/SDL_fbriva.c
Generating dependencies for ./src/video/fbcon/SDL_fbvideo.c
Generating dependencies for ./src/thread/pthread/SDL_systhread.c
Generating dependencies for ./src/thread/pthread/SDL_syssem.c
Generating dependencies for ./src/thread/pthread/SDL_sysmutex.c
Generating dependencies for ./src/thread/pthread/SDL_syscond.c
Generating dependencies for ./src/joystick/linux/SDL_sysjoystick.c
Generating dependencies for ./src/cdrom/linux/SDL_syscdrom.c
Generating dependencies for ./src/timer/unix/SDL_systimer.c
ash@ash-desktop:~/SDL-1.2.12$ make
Warning, configure.in is out of date
#(cd . && sh autogen.sh && sh configure)
ash@ash-desktop:~/SDL-1.2.12$ sudo make install
[sudo] password for ash:
Warning, configure.in is out of date
#(cd . && sh autogen.sh && sh configure)
/bin/bash ./build-scripts/mkinstalldirs /usr/local/bin
/usr/bin/install -c -m 755 sdl-config /usr/local/bin/sdl-config
/bin/bash ./build-scripts/mkinstalldirs /usr/local/include/SDL
for file in SDL.h SDL_active.h SDL_audio.h SDL_byteorder.h SDL_cdrom.h SDL_cpuinfo.h SDL_endian.h SDL_error.h SDL_events.h SDL_getenv.h SDL_joystick.h SDL_keyboard.h SDL_keysym.h SDL_loadso.h SDL_main.h SDL_mouse.h SDL_mutex.h SDL_name.h SDL_opengl.h SDL_platform.h SDL_quit.h SDL_rwops.h SDL_stdinc.h SDL_syswm.h SDL_thread.h SDL_timer.h SDL_types.h SDL_version.h SDL_video.h begin_code.h close_code.h; do \
            /usr/bin/install -c -m 644 ./include/$file /usr/local/include/SDL/$file; \
        done
/usr/bin/install -c -m 644 include/SDL_config.h /usr/local/include/SDL/SDL_config.h
/bin/bash ./build-scripts/mkinstalldirs /usr/local/lib
/bin/bash ./libtool --mode=install /usr/bin/install -c build/libSDL.la /usr/local/lib/libSDL.la
/usr/bin/install -c build/.libs/libSDL-1.2.so.0.11.1 /usr/local/lib/libSDL-1.2.so.0.11.1
(cd /usr/local/lib && { ln -s -f libSDL-1.2.so.0.11.1 libSDL-1.2.so.0 || { rm -f libSDL-1.2.so.0 && ln -s libSDL-1.2.so.0.11.1 libSDL-1.2.so.0; }; })
(cd /usr/local/lib && { ln -s -f libSDL-1.2.so.0.11.1 libSDL.so || { rm -f libSDL.so && ln -s libSDL-1.2.so.0.11.1 libSDL.so; }; })
/usr/bin/install -c build/.libs/libSDL.lai /usr/local/lib/libSDL.la
/usr/bin/install -c build/.libs/libSDL.a /usr/local/lib/libSDL.a
chmod 644 /usr/local/lib/libSDL.a
ranlib /usr/local/lib/libSDL.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/usr/bin/install -c -m 644 build/libSDLmain.a /usr/local/lib/libSDLmain.a
ranlib /usr/local/lib/libSDLmain.a
/bin/bash ./build-scripts/mkinstalldirs /usr/local/share/aclocal
/usr/bin/install -c -m 644 ./sdl.m4 /usr/local/share/aclocal/sdl.m4
/bin/bash ./build-scripts/mkinstalldirs /usr/local/lib/pkgconfig
/usr/bin/install -c -m 644 sdl.pc /usr/local/lib/pkgconfig
/bin/bash ./build-scripts/mkinstalldirs /usr/local/man/man3
for src in ./docs/man3/*.3; do \
            file=`echo $src | sed -e 's|^.*/||'`; \
            /usr/bin/install -c -m 644 $src /usr/local/man/man3/$file; 

```

---

### Post by DirtDawg on 2007-11-01
> **ohmycar said:**
> ```
ash@ash-desktop:~$ wesnoth
Battle for Wesnoth v1.2.6
Started on Wed Oct 31 18:15:16 2007

started game: 4173775318
error display: Could not initialize SDL: No available video device
Could not initialize video. Exiting.

```

that is what I am getting, but I have the latest SDL installed...

It looks to me like you may have mucked up your SDL. the Sdl libraries are shared by a wide variety of applications and it's generally a good idea to use only the sdl libraries available in the repositories. I hate to say it, but you may have done irreversable damage when you attempted to compile the sdl source. At least more damage than I know how to fix. But you may as well try.

According to the [wesnoth package page]("http://packages.ubuntu.com/gutsy/games/wesnoth"), you need the following sdl packages:
```
libsdl-image1.2
libsdl-mixer1.2 
libsdl-net1.2
libsdl1.2debian
```

Open Synaptic and search for anything with 'sdl' in the name and make sure all of these packages are installed. I assume they are since you installed Wesnoth through Synaptic, but it's a place to start. If you can find the sdl packages you compiled (hopefully you used checkinstall), you should uninstall those packages and then replace them with the packages above.

And for the record, if you want to compile something form source, you need not only the required packages, but their "package-dev" equivalents. If you were to compile Wesnoth, for example, you would need the packages above as well as libsdl-image1.2-dev and libsdl-mixer1.2-dev.

---

### Post by gcrussell1 on 2007-11-10
Looks like this has been mentioned just above, but I'm gonna pull a slight necro to make this clear for people like me who don't always read the entirety of each post:

**To compile Wesnoth (and other apps), you need the -dev versions of the packages required as well as the runtime versions, so the SDL problem people have with compiling Wesnoth can be fixed by installing the -dev versions of the relevant SDL packages.**

EDIT: Oh, and the -dev versions of freetype (libfreetype6-dev I think) and gettext - at least for BfW

---

