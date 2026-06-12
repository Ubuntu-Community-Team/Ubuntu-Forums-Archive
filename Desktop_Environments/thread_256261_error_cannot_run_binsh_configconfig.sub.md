---
title: "error: cannot run /bin/sh config/config.sub"
date: 2006-09-12
forum: Desktop Environments
---

### Post by MunchyBugs on 2006-09-12
So I'm trying to install Q Light Controller, because I am a lighting and film engineer and I wanted to use something other than a typicall lighting board and see if anything else was out there.  Q Light Controller is a piece of software that will interface with DMX controlls over USB (provided you have the dongle by Enttec (which I do)) and emulate a lighting board but (suposedly) with easier programming, etc.

I install everything I need to install to compile the program and then i get this error:

eric@marx:/qlc2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
configure: error: cannot run /bin/sh config/config.sub


This info may also be usefull:

eric@marx:/qlc2$  ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2006-08-27 13:23 /bin/sh -> bash

eric@marx:/qlc2$ ls -lL /bin/sh
-rwxr-xr-x 1 root root 664084 2006-04-21 17:51 /bin/sh

Thanks to anyone who can help me!  I'd really rather not put XP on this machine.

---

### Post by danielph on 2006-10-22
[MunchyBugs]("http://ubuntuforums.org/member.php?u=158169") did you find an answer to this. I am having the same problem with an XMMS plugin.

---

### Post by danielph on 2006-10-22
Have a look at config/config.sub. It is most likely a shortcut. Mine was a shortcut pointing to libtool. which did not exist. The solution:

```
sudo aptitude install libtool
```

---

