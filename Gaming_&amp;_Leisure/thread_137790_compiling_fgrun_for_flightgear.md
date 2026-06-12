---
title: "compiling fgrun for flightgear"
date: 2006-02-28
forum: Gaming &amp; Leisure
---

### Post by ragdon on 2006-02-28
Hi,
I'm trying to compile fgrun for flightgear, and i get an error saying that PLIB is not present...

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /home/roger/My: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for cos in -lm... yes
checking for an ANSI C-conforming const... yes
checking for X... no
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking libutil.h usability... no
checking libutil.h presence... no
checking for libutil.h... no
checking pty.h usability... yes
checking pty.h presence... yes
checking for pty.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking utmp.h usability... yes
checking utmp.h presence... yes
checking for utmp.h... yes
checking util.h usability... no
checking util.h presence... no
checking for util.h... no
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for PLIB include path...
checking for PLIB LDFLAGS...
checking for PLIB - version >= 1.8.0... not present.
configure: error: Sufficiently new version of plib not found.

```

However, when i check in synaptic, plib 1.8.4 is already installed. I've also tried uninstalling it and reinstalling it, and i still get the same error message.

Can anyone provide some help?

---

### Post by Jimmey on 2006-03-01
You'll need the development versions of PLIB. Usually, the development versions of a library have a 'dev' suffix - The one you're looking for might be called something similar to :
> libplib-dev. 

Unforunately, I'm not at an Ubuntu machine to check for you...

But I hope this helps.

EDIT:

> plib1.8.4-dev

---

### Post by ragdon on 2006-03-01
That did it, thanks.

I also needed the dev version of simgear.

---

### Post by b0rkman on 2007-11-21
Install simgear-dev WILL solve the problem :
$sudo apt-get install simgear-dev

Happy Flying!
b0rkman

---

