---
title: "lirc &amp; config.status: error: cannot find input file: Makefile.in"
date: 2006-01-09
forum: General Help
---

### Post by andrewsawyer on 2006-01-09
I have been trying to install the CVS version of lirc onto the computer in my living room.  Unfortunately, I've been getting the error:

```
config.status: error: cannot find input file: Makefile.in
``` when I run ./setup.sh

The full details are:

```
Configuration: .setup.config, executable shell script: configure.sh
Starting the generated shell script which will call configure with the right
parameters...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for mknod... /bin/mknod
checking for mkfifo... /usr/bin/mkfifo
checking for depmod... /sbin/depmod
checking for libusb-config... no
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for gethostname... yes
checking for gettimeofday... yes
checking for mkfifo... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strerror... yes
checking for strtoul... yes
checking for snprintf... yes
checking for strsep... yes
checking for vsyslog... yes
checking for daemon... yes
checking for forkpty... no
checking for forkpty in -lutil... yes
checking vga.h usability... no
checking vga.h presence... no
checking for vga.h... no
checking for X... no
checking for getopt_long... yes
checking for mktemp... yes
checking for Linux kernel sources... /lib/modules/2.6.12-10-686/build/
checking for which drivers can be installed on this system...
checking for caraca_init in -lcaraca_client... no
checking for ir_strerror in -lirman... no
checking for ir_strerror in -lirman_sw... no
checking portaudio.h usability... no
checking portaudio.h presence... no
checking for portaudio.h... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in
root@mediacentre:/usr/src/lirc#

```

I have build-essentials, automake, linux-headers, linux-source (with a symlink /usr/src/linux), libtools and autoconf.  I've searched high and low for an answer on how to fix this problem, and the nearest I've found was a posting on the Gentoo forum:

> I noticed several people used the cvs version; some with problems, some not. However, I had problems with it. I got an error at the end of configure and could not 'make'...
Code:
config.status: error: cannot find input file: Makefile.in


using the ebuild for lirc-0.7.0_pre6 the module lirc_i2c was never built. I went and made the driver in the drivers/lirc_i2c/ directory of the cvs version and threw it i /lib/modules/`uname -r`/.../i2c/ and installed the rest with the ebuild (lirc-0.7.0_pre6). I thought I would put this on here just in case anyone else had this problem.

without lirc_i2c loaded /dev/lirc/0 will not exist, also changed the entry in /etc/conf.d/lircd:

Code:
LIRCD_OPTS="-d /dev/lirc/0"

and then irw worked like a champ! 

But this is just a little beyond my level of skill.  Could someone please tell me if they know a way around this, and if so how to do it, else break down the Gentoo post into step-by-step instructions?

Many thanks,

Andy

---

### Post by zoiks on 2006-01-09
A couple of wild guesses:

1) Try installing lirc from the repos first, including "lirc-modules-source".  Maybe cvs will configure/compile with these installed.

2) Try going to /usr/src/linux, and type "make cloneconfig" and "make prepare".  Then try configurating lirc again.

Just guesses; I'd be curious if either of these work.

---

### Post by andrewsawyer on 2006-01-09
Unfortunately neither worked, but thank you for the advise anyway!

```
root@mediacentre:/usr/src/linux# apt-get install lirc-modules-source lirc
Reading package lists... Done
Building dependency tree... Done
lirc-modules-source is already the newest version.
lirc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mediacentre:/usr/src/linux#

```
```
root@mediacentre:/usr/src/linux# make cloneconfig
make[1]: *** No rule to make target `cloneconfig'.  Stop.
make: *** [cloneconfig] Error 2
root@mediacentre:/usr/src/linux# 
```

---

### Post by jpohl on 2007-02-18
Long time lurker First time poster. I registered just to post the answer to this, though this post didn't help me, many others in ubuntuforums have.


The trouble is that the Makefile.am requires automake 1.5 or greater

Edgy installed automake1.4 by default when I installed automake so this is what I did to get past this.

```

aptitude remove automake1.4
aptitude install automake1.9

root@mythtv:/usr/src/lirc# automake --version
automake (GNU automake) 1.9.6


```

Then because you had created the Makefile.am with the old version you see

```

root@mythtv:/usr/src/lirc# automake
configure.in:17: version mismatch.  This is Automake 1.9.6,
configure.in:17: but the definition used by this AM_INIT_AUTOMAKE
configure.in:17: comes from Automake 1.4-p6.  You should recreate
configure.in:17: aclocal.m4 with aclocal and run automake again.
configure.in: required file `./install-sh' not found
configure.in: required file `./missing' not found
daemons/Makefile.am: required file `./compile' not found
daemons/Makefile.am: required file `./depcomp' not found
/usr/share/automake-1.9/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.9/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.9/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.9/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL

--snip

```

so you have to go back and restart from the beginning.

[HTML]http://www.lirc.org/cvs.html[/HTML]
```

    cd lirc
    ./autogen.sh
    ./setup.sh
    make
    make install
```

The code compiled for me after that, still haven't confirmed if I got the whole thing working.

---

