---
title: "plugger wont configure"
date: 2006-07-06
forum: Desktop Environments
---

### Post by neighborlee on 2006-07-06
hi..

   Could someone suggest a workaround for this:

neighborlee@Heartseed:~/Programs/plugger-5.1.3$ ./configure
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
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for atexit in -ldl... yes
configure: error: Unable to find X11 libraries

and I do have x11 libs and dev installed, unless its some other lib its wanting no idea......

thx
nl

---

### Post by neighborlee on 2006-07-07
> **neighborlee said:**
> hi..

   Could someone suggest a workaround for this:

neighborlee@Heartseed:~/Programs/plugger-5.1.3$ ./configure
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
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for atexit in -ldl... yes
configure: error: Unable to find X11 libraries

and I do have x11 libs and dev installed, unless its some other lib its wanting no idea......

thx
nl

sorry to BUMP , but I"d really love to know whats wrong, I just dont possess the knowledge of this system to ascertain a plausible reason so I hope someone here does..

also I get similar issues with another app:

neighborlee@Heartseed:~/Programs/sharpconstruct-bin-0.12/bin$ ./sharpconstruct
./sharpconstruct: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory

yet:
whereis libglademm-2.4.so.1
libglademm-2.4.so: /usr/lib/libglademm-2.4.so.1
neighborlee@Heartseed:~/Programs/sharpconstruct-bin-0.12/bin$ file /usr/lib/libglademm-2.4.so.1
/usr/lib/libglademm-2.4.so.1: symbolic link to `libglademm-2.4.so.1.0.5

shows this..so I did:
file /usr/lib/libglademm-2.4.so.1.0.5
/usr/lib/libglademm-2.4.so.1.0.5: ELF 64-bit LSB shared object, AMD x86-64, version 1 (SYSV), stripped


im rather sure the sharpconstruct isn't a 64 bit app so therein is the problem shrug..I thought 64 bit OS"s could handle running 32 bit apps ?

if not , and running 32bit apps in 64 environments is still far from perfected, is my only option a chroot 6 bit env ?

thx
nl

---

