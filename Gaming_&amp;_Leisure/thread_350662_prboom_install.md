---
title: "prboom install"
date: 2007-01-31
forum: Gaming &amp; Leisure
---

### Post by jabberwock486 on 2007-01-31
well I have decided to fire up a game of doom.  so i downloaded a fresh copy of prboom 2.4.7.  I am useing a fresh and updated install of kubuntu 6.10.  I install the nvidia drivers and configured X, but don't really have a way to test it.  the first thing i try is seeing if i can install prboom with apt-get
so i do this (as root)
apt-get install prboom

it says no package found. also tried lxdoom, doom, prboom-2.4.7.

so i think it is time to just make it from scratch.  I make and install from source all the SDL stuff.  SDL-mixer and SDL-net.  this goes well
i then decide to compile prboom.  then i hit the roadblock.  it give me an error about OpenGL.  i have the correct drivers installed and as far as i know 3d acceleration is on, once again i have no way to test.
here is the output when i run the con figure file
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking checking whether to use x86 asm versions of some functions... yes
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
checking whether ln -s works... yes
checking for ranlib... ranlib
checking whether compiler supports -Wall... yes
checking whether compiler supports -Wno-unused... yes
checking whether compiler supports -Wno-switch... yes
checking if malloc debugging is wanted... no
checking whether compiler supports -march=native... no
checking whether compiler supports -march=i686... yes
checking whether compiler supports -Wextra... yes
checking whether compiler supports -Wno-missing-field-initializers... yes
checking whether compiler supports -Winline... yes
checking whether compiler supports -Wwrite-strings... yes
checking whether compiler supports -Wundef... yes
checking whether compiler supports -Wbad-function-cast... yes
checking whether compiler supports -Wcast-align... yes
checking whether compiler supports -Wcast-qual... yes
checking whether compiler supports -Wdeclaration-after-statement... yes
checking whether compiler supports -ffast-math... yes
checking whether compiler supports -O2... yes
checking whether compiler supports -fomit-frame-pointer... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether byte ordering is bigendian... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for uid_t in sys/types.h... yes
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
checking whether sys_siglist is declared... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for unistd.h... (cached) yes
checking asm/byteorder.h usability... yes
checking asm/byteorder.h presence... yes
checking for asm/byteorder.h... yes
checking for stricmp... no
checking for strnicmp... no
checking for getopt... yes
checking for inet_aton... yes
checking for inet_pton... yes
checking for inet_ntop... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for mmap... yes
checking for usleep... yes
checking for pow in -lm... yes
checking for OpenGL support... no
configure: error: You must have the relevant OpenGL development libraries & headers installed to compile with OpenGL support


so my question is how do i install this without the openGL support, i don't plan on using it?  or what do i need to do to correct the problem.  also is there an easier way to install prboom and if so what are the EXACT steps that one must take to do so.
that is my only problem i have found no documentation on how to actually install prboom on anything.   I see plenty of people using it but no instructions anywhere.  I can't remember how i installed it 2 years ago.

---

### Post by jabberwock486 on 2007-01-31
well i guess my problem is larger than prboom.
i though i install SDL but when i tried to install an older version of prboom (used a deb file) i got an error stating SDL was no installed on my system

here is literally what i did.
once in the SDL source directory i ran the configure file
./configure
let that run until it quit
then i used make
make
let this run until it quit
fallowed by 
make install
i didn't see any errors.


well ok.  seeing that i can't understand why this isn't working.  i am just going to ask.
what is the complete step by step instruction for installing prboom and all of its dependencies with ubuntu 6.10.  

can is use apt-get to install what i need?
such as SDL, prboom and or anything else needed to run?

what do i have to do to apt-get or how do i type it in.


sorry but 3 days of google searching and looking around has not given me much of anything.

lets pretend i know nothing about linux.  what are the complete, as in what must i type command by command and switch by switch to install prboom or ANY doom port.

---

