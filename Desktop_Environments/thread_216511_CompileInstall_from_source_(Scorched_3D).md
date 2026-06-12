---
title: "Compile/Install from source (Scorched 3D)"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Cable on 2006-07-15
I downloaded the source for Scorched 3D and I'm having trouble installing it with checkinstall.  They have directions for installing it on the site (via make install) [here]("http://www.scorched3d.co.uk/wiki/index.php/Installing_in_Linux").  I'd just like to also have a .deb of it for easy removal if need be.  Anyway, I did this (as stated on the website)
```

cd scorched/scripts
perl createAMMakefile.pl
cd ..
sh ./autogen.sh

``` 

Those steps all worked fine.  Then I  typed
```

sudo checkinstall

``` 
It started to do some things, then failed.  Here is the output of the terminal.
```

caleb@Cable:~/Install Files/Scorched 3D/scorched$ sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

basename: extra operand `3D/scorched'
Try `basename --help' for more information.


Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
true_fopen == 0 for fopen64("/proc/mounts", "r")
/bin/sh ./config.status --recheck
running /bin/sh ./configure   --no-create --no-recursion
checking build system type... true_fopen == 0 for fopen64("/proc/mounts", "r")
i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /home/caleb/Install: No such file or directory
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
checking dependency style of gcc... true_fopen == 0 for fopen64("/proc/mounts", "r")
true_fopen == 0 for fopen64("/proc/mounts", "r")
true_fopen == 0 for fopen64("/proc/mounts", "r")
gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... true_fopen == 0 for fopen64("/proc/mounts", "r")
true_fopen == 0 for fopen64("/proc/mounts", "r")
true_fopen == 0 for fopen64("/proc/mounts", "r")
gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for SDL... checking for sdl-config... no
checking for SDL - version >= 1.2.5... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.5 not found. Try [http://www.libsdl.org/](http://www.libsdl.org/)
make: *** [config.status] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

caleb@Cable:~/Install Files/Scorched 3D/scorched$

``` 
Am I just doing something stupid to cause it to not work?  Please help.  Thanks.

---

### Post by tzulberti on 2006-07-15
Scorched 3D is in the repos. Look it there. I have installed and it works fine. The package name in scorched3d...

---

### Post by Cable on 2006-07-15
> **tzulberti said:**
> Scorched 3D is in the repos. Look it there. I have installed and it works fine. The package name in scorched3d...

Indeed it is.  I have it installed.  :-P  I'd just like to install the latest version, and also I'd just like to compile it myself for the sake of learning.  This would be my first time compiling something myself.  Any guidance in that direction?

---

### Post by cptnapalm on 2006-07-15
What I *think* you need is the libsdl dev files.  Take a look in Synaptic for libsdl and pick the dev files.  Those should contain the source code which Scorched3d needs for that portion of the compile.

---

### Post by &amp;)ky#)^ on 2006-07-19
How long will we have to wait until the new version of Scorched 3D is in the repos?  Version 40 just came out a bit ago.  Without having version 40, online play is pretty much shot.  Somebody put up version 40 please!

---

### Post by mcduck on 2006-07-20
> **bluej774 said:**
> How long will we have to wait until the new version of Scorched 3D is in the repos?  Version 40 just came out a bit ago.  Without having version 40, online play is pretty much shot.  Somebody put up version 40 please!
Until the next version of Ubuntu, at least.

Between Ubuntu versions we only get security updates. But if it gets into Efty it could be backported for Dapper. You could ask in backports section of this forum.

---

