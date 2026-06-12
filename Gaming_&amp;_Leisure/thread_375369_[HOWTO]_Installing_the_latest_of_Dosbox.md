---
title: "[HOWTO] Installing the latest of Dosbox"
date: 2007-03-03
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2007-03-03
**Homepage:** [Dosbox](http://dosbox.sourceforge.net/news.php?show_news=1)
**Project page:** [Dosbox Project Site](http://sourceforge.net/projects/dosbox)
**Wiki:** [Dosbox Wiki Page](http://dosbox.sourceforge.net/wiki/index.php)
**Describtion:** DOSBox emulates an Intel x86 PC, complete with sound, graphics, mouse, modem, etc., necessary for running many old DOS games.
**Howto tested on:** Edgy x86,


Check here: [http://gaming.gwos.org/e107_plugins/content/content.php?content.39](http://gaming.gwos.org/e107_plugins/content/content.php?content.39)

---

### Post by cor2y on 2007-03-04
Thanks for the How to 
Tt works

---

### Post by futz on 2007-03-04
Followed all instructions above. All went fine. But when I go to start dosbox I get this error:
```
futz@xblade:~$ dosbox
Exit to error: Can't init SDL No available video device

```

> If you have an old version of Dosbox installed remove it first.
Had no older version installed.
> Make sure that your sourcelist is set up correctly
Not sure what needs to be done there
> your 3D video card is set up correctly and working before advancing further
Working fine. Beryl works great. 3D games work fine.

---

### Post by Perfect Storm on 2007-03-05
1) Your PC specs.
2) version of ubuntu
3) attach configure and make output.

---

### Post by futz on 2007-03-05
> **Artificial Intelligence said:**
> 1) Your PC specs.
1 - Gigabyte GA-965P-DQ6 Mainboard
1 - Mushkin HP2-6400 2x1GB 4-5-4-11-1T
1 - Intel Core 2 Duo E6600 Dual Core Conroe 2.40GHZ
1 - EVGA E-GEFORCE 7950 GT KO 560MHZ PCI-E 512MB


> 2) version of ubuntu
Ubuntu Edgy 6.10


> 3) attach configure and make output.
configure:
```
futz@xblade:/media/sdc1/download/dosbox-0.70$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for sdl-config... /usr/local/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
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
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for unsigned char... yes
checking size of unsigned char... 1
checking for unsigned short... yes
checking size of unsigned short... 2
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking for unsigned long long... yes
checking size of unsigned long long... 8
checking for int *... yes
checking size of int *... 4
checking if environ can be included... yes
checking if environ can be linked... yes
checking for powf in -lm... yes
checking if compiler allows __attribute__... yes
checking if compiler allows __builtin_expect... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
checking whether byte ordering is bigendian... no
checking for target cpu type... x86 compatible
checking whether x86 dynamic cpu core will be enabled... yes
checking whether fpu emulation will be enabled... yes
checking whether x86 assembly fpu core will be enabled... yes
checking whether to enable unaligned memory access... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_check_sig in -lpng... yes
checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
checking for SDLNet_Init in -lSDL_net... yes
configure: WARNING: Can't find SDL_net, internal modem and ipx disabled
checking whether opengl display output will be enabled... checking for main in -lGL... yes
checking for main in -lopengl32... no
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
yes
checking SDL_sound.h usability... no
checking SDL_sound.h presence... no
checking for SDL_sound.h... no
checking for Sound_Init in -lSDL_sound... yes
checking for Sound_Seek in -lSDL_sound... yes
configure: WARNING: Can't find libSDL_sound, libSDL_sound support disabled
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mprotect... yes
checking for setpriority support... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/cpu/Makefile
config.status: creating src/cpu/core_full/Makefile
config.status: creating src/cpu/core_normal/Makefile
config.status: creating src/cpu/core_dyn_x86/Makefile
config.status: creating src/debug/Makefile
config.status: creating src/dos/Makefile
config.status: creating src/fpu/Makefile
config.status: creating src/gui/Makefile
config.status: creating src/hardware/Makefile
config.status: creating src/hardware/serialport/Makefile
config.status: creating src/ints/Makefile
config.status: creating src/libs/Makefile
config.status: creating src/libs/zmbv/Makefile
config.status: creating src/misc/Makefile
config.status: creating src/shell/Makefile
config.status: creating src/platform/Makefile
config.status: creating src/platform/visualc/Makefile
config.status: creating visualc_net/Makefile
config.status: creating include/Makefile
config.status: creating docs/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```


make (warning - this is very large):
```
futz@xblade:/media/sdc1/download/dosbox-0.70$ make
make  all-recursive
make[1]: Entering directory `/media/sdc1/download/dosbox-0.70'
Making all in src
make[2]: Entering directory `/media/sdc1/download/dosbox-0.70/src'
Making all in cpu
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/cpu'
Making all in core_full
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/cpu/core_full'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/cpu/core_full'
Making all in core_normal
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/cpu/core_normal'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/cpu/core_normal'
Making all in core_dyn_x86
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/cpu/core_dyn_x86'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/cpu/core_dyn_x86'
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/cpu'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT callback.o -MD -MP -MF ".deps/callback.Tpo" \
          -c -o callback.o `test -f 'callback.cpp' || echo './'`callback.cpp; \
        then mv -f ".deps/callback.Tpo" ".deps/callback.Po"; \
        else rm -f ".deps/callback.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cpu.o -MD -MP -MF ".deps/cpu.Tpo" \
          -c -o cpu.o `test -f 'cpu.cpp' || echo './'`cpu.cpp; \
        then mv -f ".deps/cpu.Tpo" ".deps/cpu.Po"; \
        else rm -f ".deps/cpu.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT flags.o -MD -MP -MF ".deps/flags.Tpo" \
          -c -o flags.o `test -f 'flags.cpp' || echo './'`flags.cpp; \
        then mv -f ".deps/flags.Tpo" ".deps/flags.Po"; \
        else rm -f ".deps/flags.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT modrm.o -MD -MP -MF ".deps/modrm.Tpo" \
          -c -o modrm.o `test -f 'modrm.cpp' || echo './'`modrm.cpp; \
        then mv -f ".deps/modrm.Tpo" ".deps/modrm.Po"; \
        else rm -f ".deps/modrm.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT core_full.o -MD -MP -MF ".deps/core_full.Tpo" \
          -c -o core_full.o `test -f 'core_full.cpp' || echo './'`core_full.cpp; \
        then mv -f ".deps/core_full.Tpo" ".deps/core_full.Po"; \
        else rm -f ".deps/core_full.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT paging.o -MD -MP -MF ".deps/paging.Tpo" \
          -c -o paging.o `test -f 'paging.cpp' || echo './'`paging.cpp; \
        then mv -f ".deps/paging.Tpo" ".deps/paging.Po"; \
        else rm -f ".deps/paging.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT core_normal.o -MD -MP -MF ".deps/core_normal.Tpo" \
          -c -o core_normal.o `test -f 'core_normal.cpp' || echo './'`core_normal.cpp; \
        then mv -f ".deps/core_normal.Tpo" ".deps/core_normal.Po"; \
        else rm -f ".deps/core_normal.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT core_simple.o -MD -MP -MF ".deps/core_simple.Tpo" \
          -c -o core_simple.o `test -f 'core_simple.cpp' || echo './'`core_simple.cpp; \
        then mv -f ".deps/core_simple.Tpo" ".deps/core_simple.Po"; \
        else rm -f ".deps/core_simple.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT core_dyn_x86.o -MD -MP -MF ".deps/core_dyn_x86.Tpo" \
          -c -o core_dyn_x86.o `test -f 'core_dyn_x86.cpp' || echo './'`core_dyn_x86.cpp; \
        then mv -f ".deps/core_dyn_x86.Tpo" ".deps/core_dyn_x86.Po"; \
        else rm -f ".deps/core_dyn_x86.Tpo"; exit 1; \
        fi
rm -f libcpu.a
ar cru libcpu.a callback.o cpu.o flags.o modrm.o core_full.o paging.o core_normal.o core_simple.o core_dyn_x86.o 
ranlib libcpu.a
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/cpu'
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/cpu'
Making all in debug
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/debug'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT debug.o -MD -MP -MF ".deps/debug.Tpo" \
          -c -o debug.o `test -f 'debug.cpp' || echo './'`debug.cpp; \
        then mv -f ".deps/debug.Tpo" ".deps/debug.Po"; \
        else rm -f ".deps/debug.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT debug_gui.o -MD -MP -MF ".deps/debug_gui.Tpo" \
          -c -o debug_gui.o `test -f 'debug_gui.cpp' || echo './'`debug_gui.cpp; \
        then mv -f ".deps/debug_gui.Tpo" ".deps/debug_gui.Po"; \
        else rm -f ".deps/debug_gui.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT debug_disasm.o -MD -MP -MF ".deps/debug_disasm.Tpo" \
          -c -o debug_disasm.o `test -f 'debug_disasm.cpp' || echo './'`debug_disasm.cpp; \
        then mv -f ".deps/debug_disasm.Tpo" ".deps/debug_disasm.Po"; \
        else rm -f ".deps/debug_disasm.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT debug_win32.o -MD -MP -MF ".deps/debug_win32.Tpo" \
          -c -o debug_win32.o `test -f 'debug_win32.cpp' || echo './'`debug_win32.cpp; \
        then mv -f ".deps/debug_win32.Tpo" ".deps/debug_win32.Po"; \
        else rm -f ".deps/debug_win32.Tpo"; exit 1; \
        fi
rm -f libdebug.a
ar cru libdebug.a debug.o debug_gui.o debug_disasm.o debug_win32.o 
ranlib libdebug.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/debug'
Making all in dos
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/dos'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos.o -MD -MP -MF ".deps/dos.Tpo" \
          -c -o dos.o `test -f 'dos.cpp' || echo './'`dos.cpp; \
        then mv -f ".deps/dos.Tpo" ".deps/dos.Po"; \
        else rm -f ".deps/dos.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_devices.o -MD -MP -MF ".deps/dos_devices.Tpo" \
          -c -o dos_devices.o `test -f 'dos_devices.cpp' || echo './'`dos_devices.cpp; \
        then mv -f ".deps/dos_devices.Tpo" ".deps/dos_devices.Po"; \
        else rm -f ".deps/dos_devices.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_execute.o -MD -MP -MF ".deps/dos_execute.Tpo" \
          -c -o dos_execute.o `test -f 'dos_execute.cpp' || echo './'`dos_execute.cpp; \
        then mv -f ".deps/dos_execute.Tpo" ".deps/dos_execute.Po"; \
        else rm -f ".deps/dos_execute.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_files.o -MD -MP -MF ".deps/dos_files.Tpo" \
          -c -o dos_files.o `test -f 'dos_files.cpp' || echo './'`dos_files.cpp; \
        then mv -f ".deps/dos_files.Tpo" ".deps/dos_files.Po"; \
        else rm -f ".deps/dos_files.Tpo"; exit 1; \
        fi
dos_files.cpp: In function ‘Bit8u FCB_Parsename(Bit16u, Bit16u, Bit8u, char*, Bit8u*)’:
dos_files.cpp:691: warning: ‘packed’ attribute ignored for field of type ‘FCB_Parsename(Bit16u, Bit16u, Bit8u, char*, Bit8u*)::<anonymous union>::<anonymous struct>’
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_ioctl.o -MD -MP -MF ".deps/dos_ioctl.Tpo" \
          -c -o dos_ioctl.o `test -f 'dos_ioctl.cpp' || echo './'`dos_ioctl.cpp; \
        then mv -f ".deps/dos_ioctl.Tpo" ".deps/dos_ioctl.Po"; \
        else rm -f ".deps/dos_ioctl.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_memory.o -MD -MP -MF ".deps/dos_memory.Tpo" \
          -c -o dos_memory.o `test -f 'dos_memory.cpp' || echo './'`dos_memory.cpp; \
        then mv -f ".deps/dos_memory.Tpo" ".deps/dos_memory.Po"; \
        else rm -f ".deps/dos_memory.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_misc.o -MD -MP -MF ".deps/dos_misc.Tpo" \
          -c -o dos_misc.o `test -f 'dos_misc.cpp' || echo './'`dos_misc.cpp; \
        then mv -f ".deps/dos_misc.Tpo" ".deps/dos_misc.Po"; \
        else rm -f ".deps/dos_misc.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_classes.o -MD -MP -MF ".deps/dos_classes.Tpo" \
          -c -o dos_classes.o `test -f 'dos_classes.cpp' || echo './'`dos_classes.cpp; \
        then mv -f ".deps/dos_classes.Tpo" ".deps/dos_classes.Po"; \
        else rm -f ".deps/dos_classes.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_programs.o -MD -MP -MF ".deps/dos_programs.Tpo" \
          -c -o dos_programs.o `test -f 'dos_programs.cpp' || echo './'`dos_programs.cpp; \
        then mv -f ".deps/dos_programs.Tpo" ".deps/dos_programs.Po"; \
        else rm -f ".deps/dos_programs.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_tables.o -MD -MP -MF ".deps/dos_tables.Tpo" \
          -c -o dos_tables.o `test -f 'dos_tables.cpp' || echo './'`dos_tables.cpp; \
        then mv -f ".deps/dos_tables.Tpo" ".deps/dos_tables.Po"; \
        else rm -f ".deps/dos_tables.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT drives.o -MD -MP -MF ".deps/drives.Tpo" \
          -c -o drives.o `test -f 'drives.cpp' || echo './'`drives.cpp; \
        then mv -f ".deps/drives.Tpo" ".deps/drives.Po"; \
        else rm -f ".deps/drives.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT drive_virtual.o -MD -MP -MF ".deps/drive_virtual.Tpo" \
          -c -o drive_virtual.o `test -f 'drive_virtual.cpp' || echo './'`drive_virtual.cpp; \
        then mv -f ".deps/drive_virtual.Tpo" ".deps/drive_virtual.Po"; \
        else rm -f ".deps/drive_virtual.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT drive_local.o -MD -MP -MF ".deps/drive_local.Tpo" \
          -c -o drive_local.o `test -f 'drive_local.cpp' || echo './'`drive_local.cpp; \
        then mv -f ".deps/drive_local.Tpo" ".deps/drive_local.Po"; \
        else rm -f ".deps/drive_local.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT drive_cache.o -MD -MP -MF ".deps/drive_cache.Tpo" \
          -c -o drive_cache.o `test -f 'drive_cache.cpp' || echo './'`drive_cache.cpp; \
        then mv -f ".deps/drive_cache.Tpo" ".deps/drive_cache.Po"; \
        else rm -f ".deps/drive_cache.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT drive_fat.o -MD -MP -MF ".deps/drive_fat.Tpo" \
          -c -o drive_fat.o `test -f 'drive_fat.cpp' || echo './'`drive_fat.cpp; \
        then mv -f ".deps/drive_fat.Tpo" ".deps/drive_fat.Po"; \
        else rm -f ".deps/drive_fat.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT drive_iso.o -MD -MP -MF ".deps/drive_iso.Tpo" \
          -c -o drive_iso.o `test -f 'drive_iso.cpp' || echo './'`drive_iso.cpp; \
        then mv -f ".deps/drive_iso.Tpo" ".deps/drive_iso.Po"; \
        else rm -f ".deps/drive_iso.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_mscdex.o -MD -MP -MF ".deps/dos_mscdex.Tpo" \
          -c -o dos_mscdex.o `test -f 'dos_mscdex.cpp' || echo './'`dos_mscdex.cpp; \
        then mv -f ".deps/dos_mscdex.Tpo" ".deps/dos_mscdex.Po"; \
        else rm -f ".deps/dos_mscdex.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dos_keyboard_layout.o -MD -MP -MF ".deps/dos_keyboard_layout.Tpo" \
          -c -o dos_keyboard_layout.o `test -f 'dos_keyboard_layout.cpp' || echo './'`dos_keyboard_layout.cpp; \
        then mv -f ".deps/dos_keyboard_layout.Tpo" ".deps/dos_keyboard_layout.Po"; \
        else rm -f ".deps/dos_keyboard_layout.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cdrom.o -MD -MP -MF ".deps/cdrom.Tpo" \
          -c -o cdrom.o `test -f 'cdrom.cpp' || echo './'`cdrom.cpp; \
        then mv -f ".deps/cdrom.Tpo" ".deps/cdrom.Po"; \
        else rm -f ".deps/cdrom.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cdrom_ioctl_win32.o -MD -MP -MF ".deps/cdrom_ioctl_win32.Tpo" \
          -c -o cdrom_ioctl_win32.o `test -f 'cdrom_ioctl_win32.cpp' || echo './'`cdrom_ioctl_win32.cpp; \
        then mv -f ".deps/cdrom_ioctl_win32.Tpo" ".deps/cdrom_ioctl_win32.Po"; \
        else rm -f ".deps/cdrom_ioctl_win32.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cdrom_aspi_win32.o -MD -MP -MF ".deps/cdrom_aspi_win32.Tpo" \
          -c -o cdrom_aspi_win32.o `test -f 'cdrom_aspi_win32.cpp' || echo './'`cdrom_aspi_win32.cpp; \
        then mv -f ".deps/cdrom_aspi_win32.Tpo" ".deps/cdrom_aspi_win32.Po"; \
        else rm -f ".deps/cdrom_aspi_win32.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cdrom_ioctl_linux.o -MD -MP -MF ".deps/cdrom_ioctl_linux.Tpo" \
          -c -o cdrom_ioctl_linux.o `test -f 'cdrom_ioctl_linux.cpp' || echo './'`cdrom_ioctl_linux.cpp; \
        then mv -f ".deps/cdrom_ioctl_linux.Tpo" ".deps/cdrom_ioctl_linux.Po"; \
        else rm -f ".deps/cdrom_ioctl_linux.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cdrom_image.o -MD -MP -MF ".deps/cdrom_image.Tpo" \
          -c -o cdrom_image.o `test -f 'cdrom_image.cpp' || echo './'`cdrom_image.cpp; \
        then mv -f ".deps/cdrom_image.Tpo" ".deps/cdrom_image.Po"; \
        else rm -f ".deps/cdrom_image.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cdrom_ioctl_os2.o -MD -MP -MF ".deps/cdrom_ioctl_os2.Tpo" \
          -c -o cdrom_ioctl_os2.o `test -f 'cdrom_ioctl_os2.cpp' || echo './'`cdrom_ioctl_os2.cpp; \
        then mv -f ".deps/cdrom_ioctl_os2.Tpo" ".deps/cdrom_ioctl_os2.Po"; \
        else rm -f ".deps/cdrom_ioctl_os2.Tpo"; exit 1; \
        fi
rm -f libdos.a
ar cru libdos.a dos.o dos_devices.o dos_execute.o dos_files.o dos_ioctl.o dos_memory.o dos_misc.o dos_classes.o dos_programs.o dos_tables.o drives.o drive_virtual.o drive_local.o drive_cache.o drive_fat.o drive_iso.o dos_mscdex.o dos_keyboard_layout.o cdrom.o cdrom_ioctl_win32.o cdrom_aspi_win32.o cdrom_ioctl_linux.o cdrom_image.o cdrom_ioctl_os2.o 
ranlib libdos.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/dos'
Making all in fpu
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/fpu'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT fpu.o -MD -MP -MF ".deps/fpu.Tpo" \
          -c -o fpu.o `test -f 'fpu.cpp' || echo './'`fpu.cpp; \
        then mv -f ".deps/fpu.Tpo" ".deps/fpu.Po"; \
        else rm -f ".deps/fpu.Tpo"; exit 1; \
        fi
rm -f libfpu.a
ar cru libfpu.a fpu.o 
ranlib libfpu.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/fpu'
Making all in gui
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/gui'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT sdlmain.o -MD -MP -MF ".deps/sdlmain.Tpo" \
          -c -o sdlmain.o `test -f 'sdlmain.cpp' || echo './'`sdlmain.cpp; \
        then mv -f ".deps/sdlmain.Tpo" ".deps/sdlmain.Po"; \
        else rm -f ".deps/sdlmain.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT sdl_mapper.o -MD -MP -MF ".deps/sdl_mapper.Tpo" \
          -c -o sdl_mapper.o `test -f 'sdl_mapper.cpp' || echo './'`sdl_mapper.cpp; \
        then mv -f ".deps/sdl_mapper.Tpo" ".deps/sdl_mapper.Po"; \
        else rm -f ".deps/sdl_mapper.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT render.o -MD -MP -MF ".deps/render.Tpo" \
          -c -o render.o `test -f 'render.cpp' || echo './'`render.cpp; \
        then mv -f ".deps/render.Tpo" ".deps/render.Po"; \
        else rm -f ".deps/render.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT render_scalers.o -MD -MP -MF ".deps/render_scalers.Tpo" \
          -c -o render_scalers.o `test -f 'render_scalers.cpp' || echo './'`render_scalers.cpp; \
        then mv -f ".deps/render_scalers.Tpo" ".deps/render_scalers.Po"; \
        else rm -f ".deps/render_scalers.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT midi.o -MD -MP -MF ".deps/midi.Tpo" \
          -c -o midi.o `test -f 'midi.cpp' || echo './'`midi.cpp; \
        then mv -f ".deps/midi.Tpo" ".deps/midi.Po"; \
        else rm -f ".deps/midi.Tpo"; exit 1; \
        fi
rm -f libgui.a
ar cru libgui.a sdlmain.o sdl_mapper.o render.o render_scalers.o midi.o 
ranlib libgui.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/gui'
Making all in hardware
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/hardware'
Making all in serialport
```
Continued next message...

---

### Post by futz on 2007-03-05
make continued:
```
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/hardware/serialport'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT directserial_win32.o -MD -MP -MF ".deps/directserial_win32.Tpo" \
          -c -o directserial_win32.o `test -f 'directserial_win32.cpp' || echo './'`directserial_win32.cpp; \
        then mv -f ".deps/directserial_win32.Tpo" ".deps/directserial_win32.Po"; \
        else rm -f ".deps/directserial_win32.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT serialdummy.o -MD -MP -MF ".deps/serialdummy.Tpo" \
          -c -o serialdummy.o `test -f 'serialdummy.cpp' || echo './'`serialdummy.cpp; \
        then mv -f ".deps/serialdummy.Tpo" ".deps/serialdummy.Po"; \
        else rm -f ".deps/serialdummy.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT serialport.o -MD -MP -MF ".deps/serialport.Tpo" \
          -c -o serialport.o `test -f 'serialport.cpp' || echo './'`serialport.cpp; \
        then mv -f ".deps/serialport.Tpo" ".deps/serialport.Po"; \
        else rm -f ".deps/serialport.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT softmodem.o -MD -MP -MF ".deps/softmodem.Tpo" \
          -c -o softmodem.o `test -f 'softmodem.cpp' || echo './'`softmodem.cpp; \
        then mv -f ".deps/softmodem.Tpo" ".deps/softmodem.Po"; \
        else rm -f ".deps/softmodem.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT misc_util.o -MD -MP -MF ".deps/misc_util.Tpo" \
          -c -o misc_util.o `test -f 'misc_util.cpp' || echo './'`misc_util.cpp; \
        then mv -f ".deps/misc_util.Tpo" ".deps/misc_util.Po"; \
        else rm -f ".deps/misc_util.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT directserial_os2.o -MD -MP -MF ".deps/directserial_os2.Tpo" \
          -c -o directserial_os2.o `test -f 'directserial_os2.cpp' || echo './'`directserial_os2.cpp; \
        then mv -f ".deps/directserial_os2.Tpo" ".deps/directserial_os2.Po"; \
        else rm -f ".deps/directserial_os2.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT directserial_posix.o -MD -MP -MF ".deps/directserial_posix.Tpo" \
          -c -o directserial_posix.o `test -f 'directserial_posix.cpp' || echo './'`directserial_posix.cpp; \
        then mv -f ".deps/directserial_posix.Tpo" ".deps/directserial_posix.Po"; \
        else rm -f ".deps/directserial_posix.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I../../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT nullmodem.o -MD -MP -MF ".deps/nullmodem.Tpo" \
          -c -o nullmodem.o `test -f 'nullmodem.cpp' || echo './'`nullmodem.cpp; \
        then mv -f ".deps/nullmodem.Tpo" ".deps/nullmodem.Po"; \
        else rm -f ".deps/nullmodem.Tpo"; exit 1; \
        fi
rm -f libserial.a
ar cru libserial.a directserial_win32.o serialdummy.o serialport.o softmodem.o misc_util.o directserial_os2.o directserial_posix.o nullmodem.o 
ranlib libserial.a
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/hardware/serialport'
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/hardware'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT adlib.o -MD -MP -MF ".deps/adlib.Tpo" \
          -c -o adlib.o `test -f 'adlib.cpp' || echo './'`adlib.cpp; \
        then mv -f ".deps/adlib.Tpo" ".deps/adlib.Po"; \
        else rm -f ".deps/adlib.Tpo"; exit 1; \
        fi
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:375: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c:501: warning: converting to &#8216;OPL2::UINT8&#8217; from &#8216;double&#8217;
fmopl.c: In function &#8216;void OPL2::OPL_initalize(OPL2::FM_OPL*)&#8217;:
fmopl.c:1304: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:1307: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:1312: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
fmopl.c:1314: warning: converting to &#8216;OPL2::UINT32&#8217; from &#8216;double&#8217;
ymf262.c: At global scope:
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:326: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c:452: warning: converting to &#8216;THEOPL3::UINT8&#8217; from &#8216;double&#8217;
ymf262.c: In function &#8216;void THEOPL3::OPL3_initalize(THEOPL3::OPL3*)&#8217;:
ymf262.c:1347: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:1350: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:1355: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
ymf262.c:1357: warning: converting to &#8216;THEOPL3::UINT32&#8217; from &#8216;double&#8217;
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dma.o -MD -MP -MF ".deps/dma.Tpo" \
          -c -o dma.o `test -f 'dma.cpp' || echo './'`dma.cpp; \
        then mv -f ".deps/dma.Tpo" ".deps/dma.Po"; \
        else rm -f ".deps/dma.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT gameblaster.o -MD -MP -MF ".deps/gameblaster.Tpo" \
          -c -o gameblaster.o `test -f 'gameblaster.cpp' || echo './'`gameblaster.cpp; \
        then mv -f ".deps/gameblaster.Tpo" ".deps/gameblaster.Po"; \
        else rm -f ".deps/gameblaster.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT hardware.o -MD -MP -MF ".deps/hardware.Tpo" \
          -c -o hardware.o `test -f 'hardware.cpp' || echo './'`hardware.cpp; \
        then mv -f ".deps/hardware.Tpo" ".deps/hardware.Po"; \
        else rm -f ".deps/hardware.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT iohandler.o -MD -MP -MF ".deps/iohandler.Tpo" \
          -c -o iohandler.o `test -f 'iohandler.cpp' || echo './'`iohandler.cpp; \
        then mv -f ".deps/iohandler.Tpo" ".deps/iohandler.Po"; \
        else rm -f ".deps/iohandler.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT joystick.o -MD -MP -MF ".deps/joystick.Tpo" \
          -c -o joystick.o `test -f 'joystick.cpp' || echo './'`joystick.cpp; \
        then mv -f ".deps/joystick.Tpo" ".deps/joystick.Po"; \
        else rm -f ".deps/joystick.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT keyboard.o -MD -MP -MF ".deps/keyboard.Tpo" \
          -c -o keyboard.o `test -f 'keyboard.cpp' || echo './'`keyboard.cpp; \
        then mv -f ".deps/keyboard.Tpo" ".deps/keyboard.Po"; \
        else rm -f ".deps/keyboard.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT memory.o -MD -MP -MF ".deps/memory.Tpo" \
          -c -o memory.o `test -f 'memory.cpp' || echo './'`memory.cpp; \
        then mv -f ".deps/memory.Tpo" ".deps/memory.Po"; \
        else rm -f ".deps/memory.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT mixer.o -MD -MP -MF ".deps/mixer.Tpo" \
          -c -o mixer.o `test -f 'mixer.cpp' || echo './'`mixer.cpp; \
        then mv -f ".deps/mixer.Tpo" ".deps/mixer.Po"; \
        else rm -f ".deps/mixer.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT pcspeaker.o -MD -MP -MF ".deps/pcspeaker.Tpo" \
          -c -o pcspeaker.o `test -f 'pcspeaker.cpp' || echo './'`pcspeaker.cpp; \
        then mv -f ".deps/pcspeaker.Tpo" ".deps/pcspeaker.Po"; \
        else rm -f ".deps/pcspeaker.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT pic.o -MD -MP -MF ".deps/pic.Tpo" \
          -c -o pic.o `test -f 'pic.cpp' || echo './'`pic.cpp; \
        then mv -f ".deps/pic.Tpo" ".deps/pic.Po"; \
        else rm -f ".deps/pic.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT sblaster.o -MD -MP -MF ".deps/sblaster.Tpo" \
          -c -o sblaster.o `test -f 'sblaster.cpp' || echo './'`sblaster.cpp; \
        then mv -f ".deps/sblaster.Tpo" ".deps/sblaster.Po"; \
        else rm -f ".deps/sblaster.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT tandy_sound.o -MD -MP -MF ".deps/tandy_sound.Tpo" \
          -c -o tandy_sound.o `test -f 'tandy_sound.cpp' || echo './'`tandy_sound.cpp; \
        then mv -f ".deps/tandy_sound.Tpo" ".deps/tandy_sound.Po"; \
        else rm -f ".deps/tandy_sound.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT timer.o -MD -MP -MF ".deps/timer.Tpo" \
          -c -o timer.o `test -f 'timer.cpp' || echo './'`timer.cpp; \
        then mv -f ".deps/timer.Tpo" ".deps/timer.Po"; \
        else rm -f ".deps/timer.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga.o -MD -MP -MF ".deps/vga.Tpo" \
          -c -o vga.o `test -f 'vga.cpp' || echo './'`vga.cpp; \
        then mv -f ".deps/vga.Tpo" ".deps/vga.Po"; \
        else rm -f ".deps/vga.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_attr.o -MD -MP -MF ".deps/vga_attr.Tpo" \
          -c -o vga_attr.o `test -f 'vga_attr.cpp' || echo './'`vga_attr.cpp; \
        then mv -f ".deps/vga_attr.Tpo" ".deps/vga_attr.Po"; \
        else rm -f ".deps/vga_attr.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_crtc.o -MD -MP -MF ".deps/vga_crtc.Tpo" \
          -c -o vga_crtc.o `test -f 'vga_crtc.cpp' || echo './'`vga_crtc.cpp; \
        then mv -f ".deps/vga_crtc.Tpo" ".deps/vga_crtc.Po"; \
        else rm -f ".deps/vga_crtc.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_dac.o -MD -MP -MF ".deps/vga_dac.Tpo" \
          -c -o vga_dac.o `test -f 'vga_dac.cpp' || echo './'`vga_dac.cpp; \
        then mv -f ".deps/vga_dac.Tpo" ".deps/vga_dac.Po"; \
        else rm -f ".deps/vga_dac.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_draw.o -MD -MP -MF ".deps/vga_draw.Tpo" \
          -c -o vga_draw.o `test -f 'vga_draw.cpp' || echo './'`vga_draw.cpp; \
        then mv -f ".deps/vga_draw.Tpo" ".deps/vga_draw.Po"; \
        else rm -f ".deps/vga_draw.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_gfx.o -MD -MP -MF ".deps/vga_gfx.Tpo" \
          -c -o vga_gfx.o `test -f 'vga_gfx.cpp' || echo './'`vga_gfx.cpp; \
        then mv -f ".deps/vga_gfx.Tpo" ".deps/vga_gfx.Po"; \
        else rm -f ".deps/vga_gfx.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_other.o -MD -MP -MF ".deps/vga_other.Tpo" \
          -c -o vga_other.o `test -f 'vga_other.cpp' || echo './'`vga_other.cpp; \
        then mv -f ".deps/vga_other.Tpo" ".deps/vga_other.Po"; \
        else rm -f ".deps/vga_other.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_memory.o -MD -MP -MF ".deps/vga_memory.Tpo" \
          -c -o vga_memory.o `test -f 'vga_memory.cpp' || echo './'`vga_memory.cpp; \
        then mv -f ".deps/vga_memory.Tpo" ".deps/vga_memory.Po"; \
        else rm -f ".deps/vga_memory.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_misc.o -MD -MP -MF ".deps/vga_misc.Tpo" \
          -c -o vga_misc.o `test -f 'vga_misc.cpp' || echo './'`vga_misc.cpp; \
        then mv -f ".deps/vga_misc.Tpo" ".deps/vga_misc.Po"; \
        else rm -f ".deps/vga_misc.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_seq.o -MD -MP -MF ".deps/vga_seq.Tpo" \
          -c -o vga_seq.o `test -f 'vga_seq.cpp' || echo './'`vga_seq.cpp; \
        then mv -f ".deps/vga_seq.Tpo" ".deps/vga_seq.Po"; \
        else rm -f ".deps/vga_seq.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_xga.o -MD -MP -MF ".deps/vga_xga.Tpo" \
          -c -o vga_xga.o `test -f 'vga_xga.cpp' || echo './'`vga_xga.cpp; \
        then mv -f ".deps/vga_xga.Tpo" ".deps/vga_xga.Po"; \
        else rm -f ".deps/vga_xga.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT vga_s3.o -MD -MP -MF ".deps/vga_s3.Tpo" \
          -c -o vga_s3.o `test -f 'vga_s3.cpp' || echo './'`vga_s3.cpp; \
        then mv -f ".deps/vga_s3.Tpo" ".deps/vga_s3.Po"; \
        else rm -f ".deps/vga_s3.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT cmos.o -MD -MP -MF ".deps/cmos.Tpo" \
          -c -o cmos.o `test -f 'cmos.cpp' || echo './'`cmos.cpp; \
        then mv -f ".deps/cmos.Tpo" ".deps/cmos.Po"; \
        else rm -f ".deps/cmos.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT disney.o -MD -MP -MF ".deps/disney.Tpo" \
          -c -o disney.o `test -f 'disney.cpp' || echo './'`disney.cpp; \
        then mv -f ".deps/disney.Tpo" ".deps/disney.Po"; \
        else rm -f ".deps/disney.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT gus.o -MD -MP -MF ".deps/gus.Tpo" \
          -c -o gus.o `test -f 'gus.cpp' || echo './'`gus.cpp; \
        then mv -f ".deps/gus.Tpo" ".deps/gus.Po"; \
        else rm -f ".deps/gus.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT mpu401.o -MD -MP -MF ".deps/mpu401.Tpo" \
          -c -o mpu401.o `test -f 'mpu401.cpp' || echo './'`mpu401.cpp; \
        then mv -f ".deps/mpu401.Tpo" ".deps/mpu401.Po"; \
        else rm -f ".deps/mpu401.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT ipx.o -MD -MP -MF ".deps/ipx.Tpo" \
          -c -o ipx.o `test -f 'ipx.cpp' || echo './'`ipx.cpp; \
        then mv -f ".deps/ipx.Tpo" ".deps/ipx.Po"; \
        else rm -f ".deps/ipx.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT ipxserver.o -MD -MP -MF ".deps/ipxserver.Tpo" \
          -c -o ipxserver.o `test -f 'ipxserver.cpp' || echo './'`ipxserver.cpp; \
        then mv -f ".deps/ipxserver.Tpo" ".deps/ipxserver.Po"; \
        else rm -f ".deps/ipxserver.Tpo"; exit 1; \
        fi
rm -f libhardware.a
ar cru libhardware.a adlib.o dma.o gameblaster.o hardware.o iohandler.o joystick.o keyboard.o memory.o mixer.o pcspeaker.o pic.o sblaster.o tandy_sound.o timer.o vga.o vga_attr.o vga_crtc.o vga_dac.o vga_draw.o vga_gfx.o vga_other.o vga_memory.o vga_misc.o vga_seq.o vga_xga.o vga_s3.o cmos.o disney.o gus.o mpu401.o ipx.o ipxserver.o 
ranlib libhardware.a
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/hardware'
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/hardware'
Making all in libs
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/libs'

```
Continued next message

---

### Post by futz on 2007-03-05
make continued (part 3):
```
Making all in zmbv
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/libs/zmbv'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/libs/zmbv'
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/libs'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/libs'
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/libs'
Making all in ints
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/ints'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT mouse.o -MD -MP -MF ".deps/mouse.Tpo" \
          -c -o mouse.o `test -f 'mouse.cpp' || echo './'`mouse.cpp; \
        then mv -f ".deps/mouse.Tpo" ".deps/mouse.Po"; \
        else rm -f ".deps/mouse.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT xms.o -MD -MP -MF ".deps/xms.Tpo" \
          -c -o xms.o `test -f 'xms.cpp' || echo './'`xms.cpp; \
        then mv -f ".deps/xms.Tpo" ".deps/xms.Po"; \
        else rm -f ".deps/xms.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT ems.o -MD -MP -MF ".deps/ems.Tpo" \
          -c -o ems.o `test -f 'ems.cpp' || echo './'`ems.cpp; \
        then mv -f ".deps/ems.Tpo" ".deps/ems.Po"; \
        else rm -f ".deps/ems.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10.o -MD -MP -MF ".deps/int10.Tpo" \
          -c -o int10.o `test -f 'int10.cpp' || echo './'`int10.cpp; \
        then mv -f ".deps/int10.Tpo" ".deps/int10.Po"; \
        else rm -f ".deps/int10.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_char.o -MD -MP -MF ".deps/int10_char.Tpo" \
          -c -o int10_char.o `test -f 'int10_char.cpp' || echo './'`int10_char.cpp; \
        then mv -f ".deps/int10_char.Tpo" ".deps/int10_char.Po"; \
        else rm -f ".deps/int10_char.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_memory.o -MD -MP -MF ".deps/int10_memory.Tpo" \
          -c -o int10_memory.o `test -f 'int10_memory.cpp' || echo './'`int10_memory.cpp; \
        then mv -f ".deps/int10_memory.Tpo" ".deps/int10_memory.Po"; \
        else rm -f ".deps/int10_memory.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_misc.o -MD -MP -MF ".deps/int10_misc.Tpo" \
          -c -o int10_misc.o `test -f 'int10_misc.cpp' || echo './'`int10_misc.cpp; \
        then mv -f ".deps/int10_misc.Tpo" ".deps/int10_misc.Po"; \
        else rm -f ".deps/int10_misc.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_modes.o -MD -MP -MF ".deps/int10_modes.Tpo" \
          -c -o int10_modes.o `test -f 'int10_modes.cpp' || echo './'`int10_modes.cpp; \
        then mv -f ".deps/int10_modes.Tpo" ".deps/int10_modes.Po"; \
        else rm -f ".deps/int10_modes.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_vesa.o -MD -MP -MF ".deps/int10_vesa.Tpo" \
          -c -o int10_vesa.o `test -f 'int10_vesa.cpp' || echo './'`int10_vesa.cpp; \
        then mv -f ".deps/int10_vesa.Tpo" ".deps/int10_vesa.Po"; \
        else rm -f ".deps/int10_vesa.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_pal.o -MD -MP -MF ".deps/int10_pal.Tpo" \
          -c -o int10_pal.o `test -f 'int10_pal.cpp' || echo './'`int10_pal.cpp; \
        then mv -f ".deps/int10_pal.Tpo" ".deps/int10_pal.Po"; \
        else rm -f ".deps/int10_pal.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT int10_put_pixel.o -MD -MP -MF ".deps/int10_put_pixel.Tpo" \
          -c -o int10_put_pixel.o `test -f 'int10_put_pixel.cpp' || echo './'`int10_put_pixel.cpp; \
        then mv -f ".deps/int10_put_pixel.Tpo" ".deps/int10_put_pixel.Po"; \
        else rm -f ".deps/int10_put_pixel.Tpo"; exit 1; \
        fi
int10_put_pixel.cpp:24: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:24: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:24: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:24: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
int10_put_pixel.cpp:25: warning: large integer implicitly truncated to unsigned type
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT bios.o -MD -MP -MF ".deps/bios.Tpo" \
          -c -o bios.o `test -f 'bios.cpp' || echo './'`bios.cpp; \
        then mv -f ".deps/bios.Tpo" ".deps/bios.Po"; \
        else rm -f ".deps/bios.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT bios_disk.o -MD -MP -MF ".deps/bios_disk.Tpo" \
          -c -o bios_disk.o `test -f 'bios_disk.cpp' || echo './'`bios_disk.cpp; \
        then mv -f ".deps/bios_disk.Tpo" ".deps/bios_disk.Po"; \
        else rm -f ".deps/bios_disk.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT bios_keyboard.o -MD -MP -MF ".deps/bios_keyboard.Tpo" \
          -c -o bios_keyboard.o `test -f 'bios_keyboard.cpp' || echo './'`bios_keyboard.cpp; \
        then mv -f ".deps/bios_keyboard.Tpo" ".deps/bios_keyboard.Po"; \
        else rm -f ".deps/bios_keyboard.Tpo"; exit 1; \
        fi
rm -f libints.a
ar cru libints.a mouse.o xms.o ems.o int10.o int10_char.o int10_memory.o int10_misc.o int10_modes.o int10_vesa.o int10_pal.o int10_put_pixel.o bios.o bios_disk.o bios_keyboard.o 
ranlib libints.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/ints'
Making all in misc
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/misc'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT programs.o -MD -MP -MF ".deps/programs.Tpo" \
          -c -o programs.o `test -f 'programs.cpp' || echo './'`programs.cpp; \
        then mv -f ".deps/programs.Tpo" ".deps/programs.Po"; \
        else rm -f ".deps/programs.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT messages.o -MD -MP -MF ".deps/messages.Tpo" \
          -c -o messages.o `test -f 'messages.cpp' || echo './'`messages.cpp; \
        then mv -f ".deps/messages.Tpo" ".deps/messages.Po"; \
        else rm -f ".deps/messages.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT support.o -MD -MP -MF ".deps/support.Tpo" \
          -c -o support.o `test -f 'support.cpp' || echo './'`support.cpp; \
        then mv -f ".deps/support.Tpo" ".deps/support.Po"; \
        else rm -f ".deps/support.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT setup.o -MD -MP -MF ".deps/setup.Tpo" \
          -c -o setup.o `test -f 'setup.cpp' || echo './'`setup.cpp; \
        then mv -f ".deps/setup.Tpo" ".deps/setup.Po"; \
        else rm -f ".deps/setup.Tpo"; exit 1; \
        fi
rm -f libmisc.a
ar cru libmisc.a programs.o messages.o support.o setup.o 
ranlib libmisc.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/misc'
Making all in shell
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/shell'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT shell.o -MD -MP -MF ".deps/shell.Tpo" \
          -c -o shell.o `test -f 'shell.cpp' || echo './'`shell.cpp; \
        then mv -f ".deps/shell.Tpo" ".deps/shell.Po"; \
        else rm -f ".deps/shell.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT shell_batch.o -MD -MP -MF ".deps/shell_batch.Tpo" \
          -c -o shell_batch.o `test -f 'shell_batch.cpp' || echo './'`shell_batch.cpp; \
        then mv -f ".deps/shell_batch.Tpo" ".deps/shell_batch.Po"; \
        else rm -f ".deps/shell_batch.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT shell_cmds.o -MD -MP -MF ".deps/shell_cmds.Tpo" \
          -c -o shell_cmds.o `test -f 'shell_cmds.cpp' || echo './'`shell_cmds.cpp; \
        then mv -f ".deps/shell_cmds.Tpo" ".deps/shell_cmds.Po"; \
        else rm -f ".deps/shell_cmds.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT shell_misc.o -MD -MP -MF ".deps/shell_misc.Tpo" \
          -c -o shell_misc.o `test -f 'shell_misc.cpp' || echo './'`shell_misc.cpp; \
        then mv -f ".deps/shell_misc.Tpo" ".deps/shell_misc.Po"; \
        else rm -f ".deps/shell_misc.Tpo"; exit 1; \
        fi
rm -f libshell.a
ar cru libshell.a shell.o shell_batch.o shell_cmds.o shell_misc.o 
ranlib libshell.a
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/shell'
Making all in platform
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src/platform'
Making all in visualc
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/platform/visualc'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/platform/visualc'
make[4]: Entering directory `/media/sdc1/download/dosbox-0.70/src/platform'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/platform'
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src/platform'
make[3]: Entering directory `/media/sdc1/download/dosbox-0.70/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2 -MT dosbox.o -MD -MP -MF ".deps/dosbox.Tpo" \
          -c -o dosbox.o `test -f 'dosbox.cpp' || echo './'`dosbox.cpp; \
        then mv -f ".deps/dosbox.Tpo" ".deps/dosbox.Po"; \
        else rm -f ".deps/dosbox.Tpo"; exit 1; \
        fi
g++  -g -O2   -o dosbox  dosbox.o cpu/libcpu.a debug/libdebug.a dos/libdos.a fpu/libfpu.a  hardware/libhardware.a gui/libgui.a ints/libints.a misc/libmisc.a shell/libshell.a hardware/serialport/libserial.a  -lasound -lm -ldl -lpthread -L/usr/local/lib -Wl,-rpath,/usr/local/lib -lSDL -lpng -lz -lGL
make[3]: Leaving directory `/media/sdc1/download/dosbox-0.70/src'
make[2]: Leaving directory `/media/sdc1/download/dosbox-0.70/src'
Making all in include
make[2]: Entering directory `/media/sdc1/download/dosbox-0.70/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/sdc1/download/dosbox-0.70/include'
Making all in docs
make[2]: Entering directory `/media/sdc1/download/dosbox-0.70/docs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/sdc1/download/dosbox-0.70/docs'
Making all in visualc_net
make[2]: Entering directory `/media/sdc1/download/dosbox-0.70/visualc_net'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/sdc1/download/dosbox-0.70/visualc_net'
make[2]: Entering directory `/media/sdc1/download/dosbox-0.70'
make[2]: Leaving directory `/media/sdc1/download/dosbox-0.70'
make[1]: Leaving directory `/media/sdc1/download/dosbox-0.70'
```

---

### Post by yabbadabbadont on 2007-03-05
> configure: WARNING: Can't find libSDL_sound, libSDL_sound support disabled
That explains your sound issue at least.  You probably need to install libsdl-sound1.2-dev

Edit: Note that this is on Edgy.  For Dapper the version of libsdl-sound*-dev will probably be different.

---

### Post by futz on 2007-03-05
> **yabbadabbadont said:**
> That explains your sound issue at least.  You probably need to install libsdl-sound1.2-dev

Edit: Note that this is on Edgy.  For Dapper the version of libsdl-sound*-dev will probably be different.
libsdl-sound1.2-dev was already installed

```
futz@xblade:~$ sudo apt-get install libsdl-sound1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl-sound1.2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Unconscious on 2007-03-07
I've tried using dosbox for a more serious application. My employer has a bunch of old source code for which the version control system is tlib, an old dos program. The sources are kept on a samba share on a BSD box. I tried using dosbox to run tlib and get at these sources directly. Otherwise I have to use a crappy old W2k box, pscp, and fromdos to get them to my edgy box, and edit them.

The problem is that dosbox mangles the permissions on the files, so that they look like read only, when in fact they're 664 (-rw-rw-r--). Anybody have any ideas on how to fix this?

---

### Post by lulin on 2007-03-14
You probably have to install libsdl-sound1.2 (without the -dev)

---

### Post by futz on 2007-03-14
> **lulin said:**
> You probably have to install libsdl-sound1.2 (without the -dev)
Heh! That's already installed too.

---

### Post by Perfect Storm on 2007-03-18
Just wrote a better howto for dosbox at Ubuntu Gamers arena: [http://gaming.gwos.org/e107_plugins/content/content.php?content.39](http://gaming.gwos.org/e107_plugins/content/content.php?content.39)
Also the dosgui aren't there anymore, instead I've chosen Dosbox Game Launcher which is far more superior and better than dosboxgui. Check it out.

---

### Post by yabbadabbadont on 2007-03-20
> **Artificial Intelligence said:**
> Just wrote a better howto for dosbox at Ubuntu Gamers arena: [http://gaming.gwos.org/e107_plugins/content/content.php?content.39](http://gaming.gwos.org/e107_plugins/content/content.php?content.39)
Also the dosgui aren't there anymore, instead I've chosen Dosbox Game Launcher which is far more superior and better than dosboxgui. Check it out.

Thanks for the information.  It looks good.  It's nice to see you got your site back from the hackers.  :D

---

### Post by elfuego on 2007-05-23
I got the same problem as futz. Any solutions?

---

### Post by oeolycus on 2007-06-04
Could I trouble someone to explain how to uninstall a source installation of dosbox or DBGL.  There are instructions for how to upgrade DBGL, but not how to remove it entirely.  I don't know how to upgrade or uninstall dosbox when a new version comes out.

---

### Post by therock003 on 2008-06-03
I get a 404 on the guide link.

---

### Post by Perfect Storm on 2008-06-03
We've moved: [http://gaming.gwos.org/doku.php/guides:64bit:dosboxgui](http://gaming.gwos.org/doku.php/guides:64bit:dosboxgui)
Havn't been tested on 8.04 but it should be the same.

---

### Post by therock003 on 2008-06-03
Nice thanx,i will try it on my 8.04.

Other than that you punch the commands like you would on dos,and handles the setups and everything?

---

