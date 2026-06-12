---
title: "Make Problems"
date: 2005-12-30
forum: General Help
---

### Post by bhilton on 2005-12-30
I'm attempting to install ndiswrapper on a brand new Breezy installation.  It seems that make was left out of the installation along with a proper environment for compiling.  Here's a dump of what I've done.  Anybody have any ideas about what's going on and how to fix it?

Thanks,

Brad

/usr/bin/ndiswrapper-1.7$ make install
bash: make: command not found
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.0-locales libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.2MB of archives.
After unpacking 41.9MB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 56661 files and directories currently installed.)

Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...
Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up make (3.80-9) .../usr/bin/ndiswrapper-1.7$ make install
make -C driver install
make[1]: Entering directory `/usr/bin/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/bin/ndiswrapper-1.7/driver'
make: *** [install] Error 2

---

### Post by MrCheese on 2005-12-30
Do you really need to comile ndiswrapper in the first place? I have a really cheanp'n'nasty Ti-ACX111 based card which works just fine with the Breezy default ndiswrapper.

It appears you don't have the kernel sources installed or the system can't find them - try installing the source for your kernel (2.6.12-9-386).

---

### Post by bhilton on 2005-12-30
Cool I wasn't aware that Breezy came with ndiswrapper.  Wireless is working now.  I've installed the kernel source too.

Thanks.

---

