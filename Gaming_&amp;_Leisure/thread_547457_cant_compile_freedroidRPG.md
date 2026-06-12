---
title: "cant compile freedroidRPG"
date: 2007-09-10
forum: Gaming &amp; Leisure
---

### Post by Hawk__0 on 2007-09-10
I found a guide in these forums which made no difference for me.  i keep getting these errors wehn i run ./confugre:

> 
steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ sudo ./configure && make
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sin in -lm... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
configure: Checking for compulsory SDL libraries:
checking for sdl-config... no
checking for SDL - version >= 1.2.3... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.3 not found!

make: *** No rule to make target `install'.  Stop.



i dont know what SDL is but i searched for it in the package manager and found sdljump.  and some other thing.  what is it i need?

---

### Post by Perfect Storm on 2007-09-10
```
sudo aptitude install libsdl1.2-dev
```

---

### Post by Perfect Storm on 2007-09-10
I just wrote an installation guide for it: [http://gaming.gwos.org/doku.php/guides:freedroidrpg](http://gaming.gwos.org/doku.php/guides:freedroidrpg)

---

### Post by Hawk__0 on 2007-09-10
thanks for the guide! i got it all installed! unfortunately.. i still have some problems:

```

steve@steve-desktop:~/Desktop$ freedroidRPG
bash: freedroidRPG: command not found
steve@steve-desktop:~/Desktop$ freedroidrpg
bash: freedroidrpg: command not found

```

something to do with the path right? well i installed it from start to finish with your guide.

what gives?

oh, and also, at this step:
> sudo nano /usr/share/applications/freedroidRPG.desktop
i do it from the terminal and it shows up, but if i browse to that directory with the gui i dont see it (even after pressing ctrl+H to view hidden

---

### Post by Perfect Storm on 2007-09-10
Strange I just doublechecked mine. It works.

Can you post (or attach) all the terminal ins and out-puts


> sudo nano /usr/share/applications/freedroidRPG.desktop

Did you remember to save it again.  (ctrl)+(o)

---

### Post by Hawk__0 on 2007-09-10
yeah i remembered to save it... well... its long, but here's the command line output as requested. 

```

steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sin in -lm... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
configure: Checking for compulsory SDL libraries:
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.3... yes
checking for jpeg_start_compress in -ljpeg... yes
checking for compress in -lz... yes
checking for png_read_png in -lpng... yes
checking for IMG_LoadJPG_RW in -lSDL_image... yes
checking for SDLNet_Init in -lSDL_net... yes
configure: Checking for optional SDL libraries:
checking for Mix_ChannelFinished in -lSDL_mixer... yes
checking for oggpack_read in -logg... yes
checking for vorbis_block_init in -lvorbis... yes
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether we are using the Microsoft C compiler... no
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for OpenGL library... -lGL
checking for openGL libraries... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking soundcard.h usability... no
checking soundcard.h presence... no
checking for soundcard.h... no
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking return type of signal handlers... void
checking for alarm... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for memset... yes
checking for sqrt... yes
checking for strstr... yes
checking for strtok... yes
checking for alphasort... yes
checking for scandir... yes
checking for backtrace... yes
checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.2.0... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating croppy/Makefile
config.status: creating win32/Makefile
config.status: creating config.h
config.status: executing depfiles commands
steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ make
make  all-recursive
make[1]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3'
Making all in src
make[2]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT menu.o -MD -MP -MF ".deps/menu.Tpo" -c -o menu.o menu.c; \
        then mv -f ".deps/menu.Tpo" ".deps/menu.Po"; else rm -f ".deps/menu.Tpo"; exit 1; fi
menu.c:3394: fatal error: opening dependency file .deps/menu.Tpo: Permission denied
compilation terminated.
make[2]: *** [menu.o] Error 1
make[2]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3'
make: *** [all] Error 2
steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ sudo make
make  all-recursive
make[1]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3'
Making all in src
make[2]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT menu.o -MD -MP -MF ".deps/menu.Tpo" -c -o menu.o menu.c; \
        then mv -f ".deps/menu.Tpo" ".deps/menu.Po"; else rm -f ".deps/menu.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT shop.o -MD -MP -MF ".deps/shop.Tpo" -c -o shop.o shop.c; \
        then mv -f ".deps/shop.Tpo" ".deps/shop.Po"; else rm -f ".deps/shop.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT network.o -MD -MP -MF ".deps/network.Tpo" -c -o network.o network.c; \
        then mv -f ".deps/network.Tpo" ".deps/network.Po"; else rm -f ".deps/network.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT items.o -MD -MP -MF ".deps/items.Tpo" -c -o items.o items.c; \
        then mv -f ".deps/items.Tpo" ".deps/items.Po"; else rm -f ".deps/items.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT character.o -MD -MP -MF ".deps/character.Tpo" -c -o character.o character.c; \
        then mv -f ".deps/character.Tpo" ".deps/character.Po"; else rm -f ".deps/character.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT skills.o -MD -MP -MF ".deps/skills.Tpo" -c -o skills.o skills.c; \
        then mv -f ".deps/skills.Tpo" ".deps/skills.Po"; else rm -f ".deps/skills.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT saveloadgame.o -MD -MP -MF ".deps/saveloadgame.Tpo" -c -o saveloadgame.o saveloadgame.c; \
        then mv -f ".deps/saveloadgame.Tpo" ".deps/saveloadgame.Po"; else rm -f ".deps/saveloadgame.Tpo"; exit 1; fi
saveloadgame.c: In function ‘LoadGame’:
saveloadgame.c:586: warning: pointer targets in passing argument 1 of ‘MyMemmem’ differ in signedness
saveloadgame.c:586: warning: pointer targets in passing argument 3 of ‘MyMemmem’ differ in signedness
saveloadgame.c:597: warning: pointer targets in passing argument 1 of ‘MyMemmem’ differ in signedness
saveloadgame.c:597: warning: pointer targets in passing argument 3 of ‘MyMemmem’ differ in signedness
saveloadgame.c:607: warning: pointer targets in passing argument 1 of ‘MyMemmem’ differ in signedness
saveloadgame.c:607: warning: pointer targets in passing argument 3 of ‘MyMemmem’ differ in signedness
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT leveleditor.o -MD -MP -MF ".deps/leveleditor.Tpo" -c -o leveleditor.o leveleditor.c; \
        then mv -f ".deps/leveleditor.Tpo" ".deps/leveleditor.Po"; else rm -f ".deps/leveleditor.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT blocks.o -MD -MP -MF ".deps/blocks.Tpo" -c -o blocks.o blocks.c; \
        then mv -f ".deps/blocks.Tpo" ".deps/blocks.Po"; else rm -f ".deps/blocks.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT graphics.o -MD -MP -MF ".deps/graphics.Tpo" -c -o graphics.o graphics.c; \
        then mv -f ".deps/graphics.Tpo" ".deps/graphics.Po"; else rm -f ".deps/graphics.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT map.o -MD -MP -MF ".deps/map.Tpo" -c -o map.o map.c; \
        then mv -f ".deps/map.Tpo" ".deps/map.Po"; else rm -f ".deps/map.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT init.o -MD -MP -MF ".deps/init.Tpo" -c -o init.o init.c; \
        then mv -f ".deps/init.Tpo" ".deps/init.Po"; else rm -f ".deps/init.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT ship.o -MD -MP -MF ".deps/ship.Tpo" -c -o ship.o ship.c; \
        then mv -f ".deps/ship.Tpo" ".deps/ship.Po"; else rm -f ".deps/ship.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT takeover.o -MD -MP -MF ".deps/takeover.Tpo" -c -o takeover.o takeover.c; \
        then mv -f ".deps/takeover.Tpo" ".deps/takeover.Po"; else rm -f ".deps/takeover.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT bullet.o -MD -MP -MF ".deps/bullet.Tpo" -c -o bullet.o bullet.c; \
        then mv -f ".deps/bullet.Tpo" ".deps/bullet.Po"; else rm -f ".deps/bullet.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT influ.o -MD -MP -MF ".deps/influ.Tpo" -c -o influ.o influ.c; \
        then mv -f ".deps/influ.Tpo" ".deps/influ.Po"; else rm -f ".deps/influ.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT misc.o -MD -MP -MF ".deps/misc.Tpo" -c -o misc.o misc.c; \
        then mv -f ".deps/misc.Tpo" ".deps/misc.Po"; else rm -f ".deps/misc.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT text.o -MD -MP -MF ".deps/text.Tpo" -c -o text.o text.c; \
        then mv -f ".deps/text.Tpo" ".deps/text.Po"; else rm -f ".deps/text.Tpo"; exit 1; fi
text.c: In function ‘DisplayTextWithScrolling’:
text.c:516: warning: pointer targets in passing argument 1 of ‘ImprovedCheckLineBreak’ differ in signedness
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT text_public.o -MD -MP -MF ".deps/text_public.Tpo" -c -o text_public.o text_public.c; \
        then mv -f ".deps/text_public.Tpo" ".deps/text_public.Po"; else rm -f ".deps/text_public.Tpo"; exit 1; fi
text_public.c: In function ‘MyMemmem’:
text_public.c:194: warning: pointer targets in passing argument 1 of ‘strstr’ differ in signedness
text_public.c:194: warning: pointer targets in passing argument 2 of ‘strstr’ differ in signedness
text_public.c: In function ‘ReadAndMallocAndTerminateFile’:
text_public.c:350: warning: pointer targets in passing argument 1 of ‘MyMemmem’ differ in signedness
text_public.c: In function ‘ReadValueFromStringWithDefault’:
text_public.c:416: warning: assignment discards qualifiers from pointer target type
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT sound.o -MD -MP -MF ".deps/sound.Tpo" -c -o sound.o sound.c; \
        then mv -f ".deps/sound.Tpo" ".deps/sound.Po"; else rm -f ".deps/sound.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT enemy.o -MD -MP -MF ".deps/enemy.Tpo" -c -o enemy.o enemy.c; \
        then mv -f ".deps/enemy.Tpo" ".deps/enemy.Po"; else rm -f ".deps/enemy.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT input.o -MD -MP -MF ".deps/input.Tpo" -c -o input.o input.c; \
        then mv -f ".deps/input.Tpo" ".deps/input.Po"; else rm -f ".deps/input.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT hud.o -MD -MP -MF ".deps/hud.Tpo" -c -o hud.o hud.c; \
        then mv -f ".deps/hud.Tpo" ".deps/hud.Po"; else rm -f ".deps/hud.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT view.o -MD -MP -MF ".deps/view.Tpo" -c -o view.o view.c; \
        then mv -f ".deps/view.Tpo" ".deps/view.Po"; else rm -f ".deps/view.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT automap.o -MD -MP -MF ".deps/automap.Tpo" -c -o automap.o automap.c; \
        then mv -f ".deps/automap.Tpo" ".deps/automap.Po"; else rm -f ".deps/automap.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT BFont.o -MD -MP -MF ".deps/BFont.Tpo" -c -o BFont.o BFont.c; \
        then mv -f ".deps/BFont.Tpo" ".deps/BFont.Po"; else rm -f ".deps/BFont.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT SDL_rotozoom.o -MD -MP -MF ".deps/SDL_rotozoom.Tpo" -c -o SDL_rotozoom.o SDL_rotozoom.c; \
        then mv -f ".deps/SDL_rotozoom.Tpo" ".deps/SDL_rotozoom.Po"; else rm -f ".deps/SDL_rotozoom.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT open_gl.o -MD -MP -MF ".deps/open_gl.Tpo" -c -o open_gl.o open_gl.c; \
        then mv -f ".deps/open_gl.Tpo" ".deps/open_gl.Po"; else rm -f ".deps/open_gl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT mission.o -MD -MP -MF ".deps/mission.Tpo" -c -o mission.o mission.c; \
        then mv -f ".deps/mission.Tpo" ".deps/mission.Po"; else rm -f ".deps/mission.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT chat.o -MD -MP -MF ".deps/chat.Tpo" -c -o chat.o chat.c; \
        then mv -f ".deps/chat.Tpo" ".deps/chat.Po"; else rm -f ".deps/chat.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT light.o -MD -MP -MF ".deps/light.Tpo" -c -o light.o light.c; \
        then mv -f ".deps/light.Tpo" ".deps/light.Po"; else rm -f ".deps/light.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT getopt.o -MD -MP -MF ".deps/getopt.Tpo" -c -o getopt.o getopt.c; \
        then mv -f ".deps/getopt.Tpo" ".deps/getopt.Po"; else rm -f ".deps/getopt.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT getopt1.o -MD -MP -MF ".deps/getopt1.Tpo" -c -o getopt1.o getopt1.c; \
        then mv -f ".deps/getopt1.Tpo" ".deps/getopt1.Po"; else rm -f ".deps/getopt1.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT scandir.o -MD -MP -MF ".deps/scandir.Tpo" -c -o scandir.o scandir.c; \
        then mv -f ".deps/scandir.Tpo" ".deps/scandir.Po"; else rm -f ".deps/scandir.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT sound_effects.o -MD -MP -MF ".deps/sound_effects.Tpo" -c -o sound_effects.o sound_effects.c; \
        then mv -f ".deps/sound_effects.Tpo" ".deps/sound_effects.Po"; else rm -f ".deps/sound_effects.Tpo"; exit 1; fi
gcc  -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -rdynamic -o freedroidRPG  menu.o shop.o network.o items.o character.o skills.o saveloadgame.o leveleditor.o blocks.o graphics.o map.o init.o ship.o takeover.o bullet.o influ.o misc.o text.o text_public.o sound.o enemy.o input.o main.o hud.o view.o automap.o BFont.o SDL_rotozoom.o open_gl.o mission.o chat.o light.o getopt.o getopt1.o scandir.o sound_effects.o  -lvorbis -logg -lSDL_mixer -lSDL_net -lSDL_image -lpng -lz -ljpeg -lm  -L/usr/lib -lSDL -lGL  -lm
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT ItemEditor.o -MD -MP -MF ".deps/ItemEditor.Tpo" -c -o ItemEditor.o ItemEditor.c; \
        then mv -f ".deps/ItemEditor.Tpo" ".deps/ItemEditor.Po"; else rm -f ".deps/ItemEditor.Tpo"; exit 1; fi
gcc  -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -rdynamic -o ItemEditor  ItemEditor.o text_public.o -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lvorbis -logg -lSDL_mixer -lSDL_net -lSDL_image -lpng -lz -ljpeg -lm  -L/usr/lib -lSDL -lGL  -lm
make[2]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3/src'
Making all in win32
make[2]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3/win32'
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT pngtoico.o -MD -MP -MF ".deps/pngtoico.Tpo" -c -o pngtoico.o pngtoico.c; \
        then mv -f ".deps/pngtoico.Tpo" ".deps/pngtoico.Po"; else rm -f ".deps/pngtoico.Tpo"; exit 1; fi
gcc  -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -rdynamic -o pngtoico  pngtoico.o  -lvorbis -logg -lSDL_mixer -lSDL_net -lSDL_image -lpng -lz -ljpeg -lm  -L/usr/lib -lSDL -lGL  -lm
make[2]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3/win32'
Making all in croppy
make[2]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3/croppy'
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT croppy.o -MD -MP -MF ".deps/croppy.Tpo" -c -o croppy.o croppy.c; \
        then mv -f ".deps/croppy.Tpo" ".deps/croppy.Po"; else rm -f ".deps/croppy.Tpo"; exit 1; fi
gcc  -g -O2  -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -rdynamic -o croppy  croppy.o  -lvorbis -logg -lSDL_mixer -lSDL_net -lSDL_image -lpng -lz -ljpeg -lm  -L/usr/lib -lSDL -lGL  -lm
make[2]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3/croppy'
make[2]: Entering directory `/home/steve/Desktop/freedroidrpg-0.10.3'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3'
make[1]: Leaving directory `/home/steve/Desktop/freedroidrpg-0.10.3'
steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*** SIGINT received ***

Cleaning up...OK

Bye.

steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ sudo mv freedroid.png /usr/local/share/freedroidrpg
mv: cannot stat `freedroid.png': No such file or directory
steve@steve-desktop:~/Desktop/freedroidrpg-0.10.3$ cd ..
steve@steve-desktop:~/Desktop$ sudo mv freedroid.png /usr/local/share/freedroidrpg
mv: cannot stat `freedroid.png': No such file or directory
steve@steve-desktop:~/Desktop$ sudo mv guides:freedroid.png /usr/local/share/freedroidrpg
steve@steve-desktop:~/Desktop$ sudo nano /usr/share/applications/freedroidRPG.desktop
steve@steve-desktop:~/Desktop$ freedroidRPG
bash: freedroidRPG: command not found
steve@steve-desktop:~/Desktop$ freedroidrpg
bash: freedroidrpg: command not found
steve@steve-desktop:~/Desktop$ 
steve@steve-desktop:~/Desktop$ sudo nano /usr/share/applications/freedroidRPG.desktop
Password:
Sorry, try again.
Password:
steve@steve-desktop:~/Desktop$ 


```

---

### Post by Perfect Storm on 2007-09-11
ok, it seems that the checkinstall on your system didn't work for some reason.
So instead of where it says **sudo checkinstall** use **sudo make install** in the guide.

and you have to rename the icon to freedroid.png (for some reason when saved on the wiki, it renames it).

---

### Post by Hawk__0 on 2007-09-11
thanks! it worked!

---

### Post by Perfect Storm on 2007-09-11
My please ^_^
Please check out my other guides there (if you find error or something you don't understand don't hesitate to use UGA forum for help).

guides: [http://gaming.gwos.org/doku.php/guides:guides](http://gaming.gwos.org/doku.php/guides:guides)

Our forum (sub forum on this board): [http://ubuntuforums.org/forumdisplay.php?f=230](http://ubuntuforums.org/forumdisplay.php?f=230)

---

