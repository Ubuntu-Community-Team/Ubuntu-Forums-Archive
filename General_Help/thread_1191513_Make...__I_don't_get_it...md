---
title: "Make...  I don't get it.."
date: 2009-06-19
forum: General Help
---

### Post by AoSteve on 2009-06-19
In the last two days I've tried compiling a few different things.  I've tried three different things today alone and it always comes up with the same results.  I tried installing a plugin for pidgin just a few minutes ago (seeing as how it was source) to get the results before I posted.  I'm using the music tracker plugin for this..

I open my terminal, and as per almost everyone knows,  tar the file to open the directory.  This is my progress from there...  I'm pretty sure I'm doing this right too...

***sudo ./configure***

```

steve@E8400:~/pidgin-musictracker-0.4.13.orig$ sudo ./configure
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
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PIDGIN... no
configure: error:
*** Pidgin 2.0+ is required to build MusicTracker; please make sure you have the
*** Pidgin development files installed. The latest version of Pidgin is always
*** available at http://pidgin.im/.
steve@E8400:~/pidgin-musictracker-0.4.13.orig$ 

```The I make?

```

steve@E8400:~/pidgin-musictracker-0.4.13.orig$ make
make: *** No targets specified and no makefile found.  Stop.
steve@E8400:~/pidgin-musictracker-0.4.13.orig$ 

```

Is there something I'm doing wrong?  I mean, from the compiles I've done before like this, I've never had any errors like this happen.  Wierd thing is, pidgin is actually installed and is version 2.5.5 ...

Maybe someone knows what I'm doing wrong.

---

### Post by Chronon on 2009-06-19
Hi.

The configure script is failing to find Pidgin development files.  
```
configure: error:
*** Pidgin 2.0+ is required to build MusicTracker; please make sure you have the
*** Pidgin development files installed. The latest version of Pidgin is always
*** available at http://pidgin.im/.
```

Thus it exits without generating a Makefile and make doesn't know what to do when you run it.

---

### Post by ad_267 on 2009-06-19
There is no makefile because the configure script failed. Running the configure script generates the makefile. 

> checking for PIDGIN... no
configure: error:
*** Pidgin 2.0+ is required to build MusicTracker; please make sure you have the
*** Pidgin development files installed. The latest version of Pidgin is always
*** available at [http://pidgin.im/](http://pidgin.im/).

Based on that error, you should install the pidgin-dev package. Note that when compiling a program and it says a package is required, you need the development package too, with the "-dev" suffix.

---

### Post by AoSteve on 2009-06-19
So it's basically searching for those packages and can't find them, then pop.. "Hey, I can't instruct **make** to do what it needs so I'm not going to make the makefiles."   

I think that's what I am getting from this.   How do I find out exactly what packages that I'll need?   Like, how would I know that I need that certain package?

---

### Post by Chronon on 2009-06-19
In my opinion, the configure script's error message is quite descriptive.

---

### Post by AoSteve on 2009-06-19
So, I should "hypothetically" be able to figure out which file(s) I'll need through it's errors in the terminal?

I do appreciate it.  Been a linux user for a while now, just never got into compiling as it wasn't ever "deemed" safe in my book.  But hey, I gotta learn this stuff sometime! :)   

Thanks again!

---

### Post by ad_267 on 2009-06-19
Yes, usually it's pretty obvious what packages you need to install, sometimes it takes a little guess work. Just remember to get the "-dev" packages. Usually there's also an INSTALL or a README file which may tell you what packages you need to compile the application. One handy trick if you want to compile something where a previous version already exists in the repositories is using "apt-get install build-dep package_name" which will install all of the build depenencies of a package.

Also, you shouldn't ever run the configure script as root, ie. use "./configure", not "sudo ./configure". That will only cause you problems.

You only use sudo when you run "sudo make install", as you will need root permission to copy files over to the installation directories.

---

### Post by AoSteve on 2009-06-19
The only reason I was using "sudo" was because it said that the permission was denied.  :\     I'm learning.   I'm usually a GUI kind of guy anymore, never had a lot of time working with the CLI of Linux being in school and having a full time job.  Since I'm laid off and I got time, I can really dedicate some learning time.

Thanks a BUNCH guys.  I got the dev packages from that command you showed me and it installed properly.  It actually works with pidgin now LOL   One good experience down, many new ones to learn.   Can't be that difficult comparing my knowledge I've learned in the last year with my CCNA courses.  Also a massive history behind me with DOS..  Oh god.. DOS...   Disk Operating System, or was it Dum-dum Operating System.  :)   I can't tell you how many people I had come up to me to fix thier computers when a they borked thier windows installs and it left them at a dos prompt!  :)

Like I said, thanks for the help!   I'll get it.   I've already got SH working with all three of my linux based machines in the house!  Now to learn compiling...  It's new, but I'll get it!

---

### Post by ad_267 on 2009-06-19
> **AoSteve said:**
> The only reason I was using "sudo" was because it said that the permission was denied.

That could happen after running it with sudo once. After after that you wouldn't be able to run it again without sudo as the log files and make files would all be owned by root. It could also be that the configure script wasn't executable. In which case you could run "chmod a+x configure" to make it executable for all users.

Good to hear you've got it working and you're enjoying learning! :)

---

### Post by Chronon on 2009-06-19
Congrats!  It's a good feeling to successfully build from source for the first time, isn't it?  :)

It's a big hurdle out of the way, I think.  Now it's only a very tiny step to be able to apply patches and roll your own custom binaries.

---

### Post by AoSteve on 2009-06-19
Well, it's not the first time I've ever got from source before.  First time I installed 7.10 on my old Athlon, my video drivers...  I had some help of a good friend and an instant messenger, but we compiled the nVidia drivers!

This is the first real solo set I've done without really seeing much for directions.  :)

I appreciate it a lot guys! :)   This is why Linux > M$

---

