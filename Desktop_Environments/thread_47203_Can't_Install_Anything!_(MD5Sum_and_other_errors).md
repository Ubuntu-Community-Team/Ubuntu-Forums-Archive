---
title: "Can't Install Anything! (MD5Sum and other errors)"
date: 2005-07-07
forum: Desktop Environments
---

### Post by tjleeland on 2005-07-07
I just started using Ubuntu and it appears to be the best distro I've found so far. I just have one big problem with it, and that's installing apps. Every time I've sat down to try and use Linux full-time (dumping MS) I always find myself in the same place: application depenency h*ll.

I'm once again about to dump Linux and go back to Windows over this problem, even though it looked like this time I'd found a distro that got it right. But all these packages that won't install because of MD5Sum Mismatch errors are killing me! 

I can't install a host of applications, and I can't upgrade a bunch more, and it's keeping me from installing others that depend on them - which just puts me back in dependency h*ll, like all the other times. I'm spending hours trying to hunt down source files, and the dependencies for those source files. 

Now my computer is a mess, full of half installed apps that won't work because some other app I've never heard of needs to be installed, but I can't find the source and the repository gives me a MD5 error - just like the .deb package does...

 ](*,)  I just can't take it anymore!

While looking around (and spending hours researchng the problem) I've seen messages from way back in May talking about MD5Sum errors. The solutions I've found work sometimes, but not often enough to help me out this hole, and in fact, may have helped me dig this hole even deeper. 

So why is this happening? Is it is going to be fixed, and if so, when? It appears the problem is already months old. I really don't want to put this away and say "next year" yet again, but if I can't install the types of apps I need to do my job, I won't have a choice. 

Can someone save me? Can someone rescue me from this h*ll when I'm finally so close to converting to Linux?

Thanks for any help that might be forthcoming!

TJLeeland

---

### Post by alastair on 2005-07-07
I've not had any problem myself. But I suspect I don't use half the obscure apps some folks use.

If this is an "apt" (or synaptic) problem perhaps, post a copy of your /etc/apt/sources.list

Explain what you are trying to install. And I assume this is Ubuntu 5 (Hoary).

---

### Post by tjleeland on 2005-07-07
[B]Thanks Alastair:

Yes, I'm using 5.04. OK, this is going to be messy, I'm sure. I found a lot of these as I looked around, but I added them to try and "fix" the MD5Sum problem - as opposed to them causing it. Of course, like I said before, they may have made things worse.[/B]

========== Start sources.list ==========

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

========== End sources.list ==========


[B]I'm trying to upgrade packages, originally to install some app, but I don't even remember which one. Now I just want to figure out how to upgrade the apps.

The packages are:[/B]

_To be installed:_
  libdivxdecore0
  libdivxencore0

_Unchanged:_
  libavcodeccvs
  libpostproc0
  libxvidcore4
  lsdvd
  mencoder-586
  mplayer-386
  transcode

**But I get the error:**

E: /var/cache/apt/archives/libdivxdecore0_1-0x1.6f78200000058p-1365.0.1-1_i386.deb:  trying to overwrite `/usr/lib/libdivxdecore.so', which is also in package libdivx4linux
E: /var/cache/apt/archives/libdivxencore0_1-0x1.6f78200000058p-1365.0.1-1_i386.deb:  trying to overwrite `/usr/lib/libdivxencore.so', which is also in package libdivx4linux

**This is my latest error. I have others, some of which are with source instead of Synaptic. For example, I was tying to install atk 1.9.0. When I run ./configure I get the following:** 

========== start =========

checking for GLIB - version >= 2.5.7...
*** 'pkg-config --modversion glib-2.0' returned 2.6.5, but GLIB (2.6.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

========== end ==========


[B]The above is what seemed important, but I don't know if it really means anything or if it's the result of some other thing higher in the file.

The whole thing is:[/B]

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fl32... no
checking for af77... no
checking for fort77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for lf95... no
checking for g95... no
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
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking for some Win32 platform... no
checking for native Win32 platform... no
checking for aclocal flags...
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.5.7...
*** 'pkg-config --modversion glib-2.0' returned 2.6.5, but GLIB (2.6.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.


Thanks!

---

### Post by NeoSNightmarE on 2005-07-07
heres how you fix this. you go to terminal and type in the following:

"sudo gedit /etc/apt/sources.list"

then that will bring that file up that you posted with all the different places to get the files from. then you remove the us from all of the us.archive.ubuntu.com's and run the apt-get update command (sudo apt-get update) from the terminal and it will be fixed. :)

---

### Post by darkmatter on 2005-07-07
[QUOTE=tjleeland]
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main[/quote]

You may want to comment those out. They don't always seem to like Ubuntu.

---

### Post by tjleeland on 2005-07-08
OK, I did both, commented out the **nerim.net** repostitories and removed **"us"** from every line that had it.

Is there a way to start the Ubuntu install with a sources.list file that doesn't have **"us"** in the url? Is this based on the location you give during the install? If I did a UK install or a Canadian, would I have something other than **us.archive.ubuntu.com**, like maybe **uk.archive.ubuntu.com** or **ca.archive.ubuntu.com**? Or maybe just a way to remove the **"us"** before Ubuntu tries to download packages?

If so, I think I might just start my whole install over new that I have this inforamtion. I'm not sure I can even remember all the things I've installed trying to work around the MD5Sum error, and **atk 1.90** still gives the same error (not surprisingly). 

Thanks to everyone for your help.

---

### Post by darkmatter on 2005-07-08
[QUOTE=tjleeland]Is this based on the location you give during the install?[/quote]
Yes...
[quote=tjleeland]If I did a UK install or a Canadian, would I have something other than **us.archive.ubuntu.com**, like maybe **uk.archive.ubuntu.com** or **ca.archive.ubuntu.com**?[/quote]

and yes. The only difference in sources.list in a fresh Ubuntu install is the regional prefix for the archive repository.

---

### Post by alastair on 2005-07-08
This is my sources.list :

```

deb file:/mnt/hoary/ hoary main restricted
 
deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted
 
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
 
deb http://gb.archive.ubuntu.com/ubuntu hoary universe
deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe
 
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
 
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

```

I am not sure about Marillat. It is where I got my xine/mplayer/dvd programs I think, but seems to be deprecated. I have the following commented :

```

# deb ftp://ftp.nerim.net/debian-marillat/ unstable main

```

---

### Post by tjleeland on 2005-07-08
Thanks everyone! I installed Ubuntu using the UK settings and things are much better. I've got Ethereal, nmap, hping, airsnort, and aircrack all going with no fuss, no muss.  I need those as a minimum, if I have problems with anything else I can at least take my time with them.

---

