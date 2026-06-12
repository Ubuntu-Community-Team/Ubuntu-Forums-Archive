---
title: "Problem Installing a tar.gz file."
date: 2011-03-05
forum: Desktop Environments
---

### Post by manishlogan on 2011-03-05
Hi, recently I downloaded warzone 2100. It was downloaded in tar.gz format. I searched for the way to install it and I am not able to install it.

I unzipped the folder and then changed my directory to the unzipped folder. After that I used ./configure.
After doing this, when I write make, it gives error and says no make file found. What can I do to solve this problem. 
Thanks in advance.

---

### Post by Frogs Hair on 2011-03-05
Try  sudo make if you haven't already . I have not seen the no make file error before. Here is a tutorial that may help.[www.linuxtutorialblog.com/post/troubleshooting-configure-make-and-make-install-tutorial](www.linuxtutorialblog.com/post/troubleshooting-configure-make-and-make-install-tutorial)

---

### Post by oldos2er on 2011-03-05
Don't use 'sudo' with 'make'. It sounds like ./configure didn't run successfully, so didn't create a make file. Can you post the output of ./configure ?

---

### Post by manishlogan on 2011-03-06
The output of ./configure is:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for bison... bison -y
checking for bison >= 1.31... found 2.4.1, ok
checking for flex... no
checking for lex... no
checking for : >= 2.5.33... ./configure: line 5111: [: : integer expression expected
./configure: line 5113: [: : integer expression expected
found , ok
checking for : != 2.5.34... ./configure: line 5141: [: : integer expression expected
not found, good
checking whether perl executable path has been provided... no
checking for perl... /usr/bin/perl
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for perl version... 5.10.1
checking for gawk... (cached) gawk
checking for zip... zip
checking for unzip... unzip
.
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for strlcpy... no
checking for strlcat... no
checking whether gcc -std=gnu99 accepts -fstack-protector... yes
checking whether g++ accepts -fstack-protector... yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for pkg-config >= 0.9... found 0.22, ok
checking whether to build NSIS installer... no
checking whether to compile in debug mode... no
checking whether the C compiler accepts the -Werror -Wno-switch flag... yes
checking whether the C compiler accepts the -Werror -Wno-enum-compare flag... no
checking for SDL... configure: error: Package requirements (sdl >= 1.2) were not met:

No package 'sdl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SDL_CFLAGS
and SDL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by oldos2er on 2011-03-06
See [http://developer.wz2100.net/wiki/CompileGuideLinux](http://developer.wz2100.net/wiki/CompileGuideLinux) for a list of dependencies, among other things.

---

### Post by manishlogan on 2011-03-20
I tried the link, but still its giving error in installing the SDL package. I don't know what to do for that. Have installed the game though, but want to know how to install using a tar.gz file.

---

### Post by oldos2er on 2011-03-20
**libsdl1.2-dev** is one of the dependencies, have you installed it?

---

### Post by gordintoronto on 2011-03-20
Wouldn't it be a lot easier to run Administration/Synaptic Package Manager, and install warzone from there?

---

### Post by manishlogan on 2011-03-21
> **gordintoronto said:**
> Wouldn't it be a lot easier to run Administration/Synaptic Package Manager, and install warzone from there?
I have installed it from there but still want to learn how to work with tar.gz files

---

### Post by manishlogan on 2011-03-21
> **oldos2er said:**
> **libsdl1.2-dev** is one of the dependencies, have you installed it?
Its installation is giving error.

---

### Post by oldos2er on 2011-03-22
> **manishlogan said:**
> Its installation is giving error.

And the error is...?

---

### Post by manishlogan on 2011-03-22
> **oldos2er said:**
> And the error is...?
Everything else is getting downloaded, but when I install this package, I get error: Unable to fetch data, check your network connection.

---

### Post by oldos2er on 2011-03-22
[http://packages.ubuntu.com/lucid/i386/libsdl1.2-dev/download](http://packages.ubuntu.com/lucid/i386/libsdl1.2-dev/download) or for 64-bit [http://packages.ubuntu.com/lucid/amd64/libsdl1.2-dev/download](http://packages.ubuntu.com/lucid/amd64/libsdl1.2-dev/download)

---

### Post by manishlogan on 2011-03-23
> **oldos2er said:**
> [http://packages.ubuntu.com/lucid/i386/libsdl1.2-dev/download](http://packages.ubuntu.com/lucid/i386/libsdl1.2-dev/download) or for 64-bit [http://packages.ubuntu.com/lucid/amd64/libsdl1.2-dev/download](http://packages.ubuntu.com/lucid/amd64/libsdl1.2-dev/download)
Thanx Man

---

### Post by oldos2er on 2011-03-23
Did it work?

---

