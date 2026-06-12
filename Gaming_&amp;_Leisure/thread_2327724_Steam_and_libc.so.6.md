---
title: "Steam and libc.so.6"
date: 2016-06-13
forum: Gaming &amp; Leisure
---

### Post by rbfx4x on 2016-06-13
I'm having trouble with steam.  

```
jafar@neltharion:~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Error: You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6
Error: Couldn't find bootstrap, it's not safe to reset Steam. Please contact technical support.

```

So I try to install libc.so.6 


```
jafar@neltharion:~$ sudo apt-get install ^libc6.*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libc6.1-dev-hppa-cross' for regex '^libc6.*'
Note, selecting 'libc6-armhf-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-s390x-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-armhf-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-s390-s390x-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-arm64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-armel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-s390x-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6-ppc64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-sparc-sparc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-armhf-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-ppc64-powerpc-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-x32' for regex '^libc6.*'
Note, selecting 'libc6-dbg-ppc64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-armel-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6-ppc64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-powerpc-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-m68k-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-i386' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-alpha-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-armhf-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg' for regex '^libc6.*'
Note, selecting 'libc6-dev' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-ppc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-arm64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-arm64-cross' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-powerpc-ppc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-pic' for regex '^libc6.*'
Note, selecting 'libc6-dev-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6-powerpc-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-armel-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-hppa-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-armel-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbgsym' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-powerpcspe-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-sh4-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6' for regex '^libc6.*'
Note, selecting 'libc6-dev-hppa-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-powerpc-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-sparc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-hppa-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-powerpc-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-s390-s390x-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-ppc64-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-m68k-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-armel-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-ppc64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-s390-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-m68k-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-powerpcspe-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-powerpc-ppc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-pic' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-sparc-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-alpha-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dbg-alpha-cross' for regex '^libc6.*'
Note, selecting 'libc6-m68k-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-sh4-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-arm64-cross' for regex '^libc6.*'
Note, selecting 'libc6-powerpcspe-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-ppc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-alpha-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-ppc64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-ppc64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-s390x-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips32-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-alpha-cross' for regex '^libc6.*'
Note, selecting 'libc6-x32' for regex '^libc6.*'
Note, selecting 'libc6-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-sparc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips32-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-armel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-arm64-cross' for regex '^libc6.*'
Note, selecting 'libc6-xen:i386' for regex '^libc6.*'
Note, selecting 'libc6-mips32-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6.1' for regex '^libc6.*'
Note, selecting 'libc6-hppa-cross' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-armhf-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips32-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips32-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-i386' for regex '^libc6.*'
Note, selecting 'libc6-dev-ppc64-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-sh4-cross' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-powerpcspe-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-amd64' for regex '^libc6.*'
Note, selecting 'libc6-dev-arm64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips32-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-powerpc-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-powerpc-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-i686:i386' for regex '^libc6.*'
Note, selecting 'libc6-dbg-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-alpha-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips32-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-hppa-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips64-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-hppa-cross' for regex '^libc6.*'
Note, selecting 'libc6-m68k-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-sparc64-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-sh4-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dev-ppc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips32-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-m68k-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-sh4-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-m68k-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-powerpcspe-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64-mips-cross' for regex '^libc6.*'
Note, selecting 'libc6-sparc-sparc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-ppc64-powerpc-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-powerpcspe-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips32-mips64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-armhf-armel-cross' for regex '^libc6.*'
Note, selecting 'libc6-sparc64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-s390x-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-sh4-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mips64el-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mipsn32-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-powerpc-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6.1-dbg-alpha-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-dbg-sh4-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev-armhf-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-powerpcspe-dcv1' for regex '^libc6.*'
Note, selecting 'libc6.1-dev' for regex '^libc6.*'
Note, selecting 'libc6-dev-ppc64el-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-armel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-sparc-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-mips32-mips64-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mipsel-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-armhf-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-ppc64-ppc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-arm64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dev-amd64:i386' for regex '^libc6.*'
Note, selecting 'libc6-loongson2f-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-sparcv9b-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-dbg-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-mipsn32-mips-dcv1' for regex '^libc6.*'
Note, selecting 'libc6-mips64-mipsel-cross' for regex '^libc6.*'
Note, selecting 'libc6-sparc64-cross' for regex '^libc6.*'
Note, selecting 'libc6-s390-s390x-cross' for regex '^libc6.*'
Note, selecting 'libc6-arm64-cross' instead of 'libc6-arm64-dcv1'
Note, selecting 'libc6-armhf-cross' instead of 'libc6-armhf-armhf-cross'
Note, selecting 'libc6-armhf-cross' instead of 'libc6-armhf-dcv1'
Note, selecting 'libc6-dev-arm64-cross' instead of 'libc6-dev-arm64-dcv1'
Note, selecting 'libc6-dev-armhf-cross' instead of 'libc6-dev-armhf-armhf-cross'
Note, selecting 'libc6-dev-armhf-cross' instead of 'libc6-dev-armhf-dcv1'
Note, selecting 'libc6-dev-powerpc-cross' instead of 'libc6-dev-powerpc-dcv1'
Note, selecting 'libc6-dev-ppc64el-cross' instead of 'libc6-dev-ppc64el-dcv1'
Note, selecting 'libc6-powerpc-cross' instead of 'libc6-powerpc-dcv1'
Note, selecting 'libc6-ppc64el-cross' instead of 'libc6-ppc64el-dcv1'
Note, selecting 'libc6:i386' instead of 'libc6-xen:i386'
Note, selecting 'libc6:i386' instead of 'libc6-i686:i386'
Note, selecting 'libc6.1-dev-alpha-cross' instead of 'libc6-dev-alpha-cross'
Note, selecting 'libc6-armel-cross' instead of 'libc6-armel-armel-cross'
Note, selecting 'libc6-armel-cross' instead of 'libc6-armel-dcv1'
Note, selecting 'libc6-dbg-arm64-cross' instead of 'libc6-dbg-arm64-dcv1'
Note, selecting 'libc6-dbg-armel-cross' instead of 'libc6-dbg-armel-dcv1'
Note, selecting 'libc6-dbg-armhf-cross' instead of 'libc6-dbg-armhf-dcv1'
Note, selecting 'libc6-dbg-hppa-cross' instead of 'libc6-dbg-hppa-dcv1'
Note, selecting 'libc6-dbg-m68k-cross' instead of 'libc6-dbg-m68k-dcv1'
Note, selecting 'libc6-dbg-mips-cross' instead of 'libc6-dbg-mips-dcv1'
Note, selecting 'libc6-dbg-mips64-cross' instead of 'libc6-dbg-mips64-dcv1'
Note, selecting 'libc6-dbg-mips64el-cross' instead of 'libc6-dbg-mips64el-dcv1'
Note, selecting 'libc6-dbg-mipsel-cross' instead of 'libc6-dbg-mipsel-dcv1'
Note, selecting 'libc6-dbg-powerpc-cross' instead of 'libc6-dbg-powerpc-dcv1'
Note, selecting 'libc6-dbg-powerpcspe-cross' instead of 'libc6-dbg-powerpcspe-dcv1'
Note, selecting 'libc6-dbg-ppc64-cross' instead of 'libc6-dbg-ppc64-dcv1'
Note, selecting 'libc6-dbg-ppc64el-cross' instead of 'libc6-dbg-ppc64el-dcv1'
Note, selecting 'libc6-dbg-s390x-cross' instead of 'libc6-dbg-s390x-dcv1'
Note, selecting 'libc6-dbg-sh4-cross' instead of 'libc6-dbg-sh4-dcv1'
Note, selecting 'libc6-dbg-sparc64-cross' instead of 'libc6-dbg-sparc64-dcv1'
Note, selecting 'libc6-dev-armel-cross' instead of 'libc6-dev-armel-armel-cross'
Note, selecting 'libc6-dev-armel-cross' instead of 'libc6-dev-armel-dcv1'
Note, selecting 'libc6-dev-hppa-cross' instead of 'libc6-dev-hppa-dcv1'
Note, selecting 'libc6-dev-m68k-cross' instead of 'libc6-dev-m68k-dcv1'
Note, selecting 'libc6-dev-mips-cross' instead of 'libc6-dev-mips-dcv1'
Note, selecting 'libc6-dev-mips32-mips64-cross' instead of 'libc6-dev-mips32-mips64-dcv1'
Note, selecting 'libc6-dev-mips32-mips64el-cross' instead of 'libc6-dev-mips32-mips64el-dcv1'
Note, selecting 'libc6-dev-mips64-cross' instead of 'libc6-dev-mips64-dcv1'
Note, selecting 'libc6-dev-mips64-mips-cross' instead of 'libc6-dev-mips64-mips-dcv1'
Note, selecting 'libc6-dev-mips64-mipsel-cross' instead of 'libc6-dev-mips64-mipsel-dcv1'
Note, selecting 'libc6-dev-mips64el-cross' instead of 'libc6-dev-mips64el-dcv1'
Note, selecting 'libc6-dev-mipsel-cross' instead of 'libc6-dev-mipsel-dcv1'
Note, selecting 'libc6-dev-mipsn32-mips-cross' instead of 'libc6-dev-mipsn32-mips-dcv1'
Note, selecting 'libc6-dev-mipsn32-mips64-cross' instead of 'libc6-dev-mipsn32-mips64-dcv1'
Note, selecting 'libc6-dev-mipsn32-mips64el-cross' instead of 'libc6-dev-mipsn32-mips64el-dcv1'
Note, selecting 'libc6-dev-mipsn32-mipsel-cross' instead of 'libc6-dev-mipsn32-mipsel-dcv1'
Note, selecting 'libc6-dev-powerpc-ppc64-cross' instead of 'libc6-dev-powerpc-ppc64-dcv1'
Note, selecting 'libc6-dev-powerpcspe-cross' instead of 'libc6-dev-powerpcspe-dcv1'
Note, selecting 'libc6-dev-ppc64-cross' instead of 'libc6-dev-ppc64-dcv1'
Note, selecting 'libc6-dev-ppc64-powerpc-cross' instead of 'libc6-dev-ppc64-powerpc-dcv1'
Note, selecting 'libc6-dev-s390-s390x-cross' instead of 'libc6-dev-s390-s390x-dcv1'
Note, selecting 'libc6-dev-s390x-cross' instead of 'libc6-dev-s390x-dcv1'
Note, selecting 'libc6-dev-sh4-cross' instead of 'libc6-dev-sh4-dcv1'
Note, selecting 'libc6-dev-sparc-sparc64-cross' instead of 'libc6-dev-sparc-sparc64-dcv1'
Note, selecting 'libc6-dev-sparc64-cross' instead of 'libc6-dev-sparc64-dcv1'
Note, selecting 'libc6-hppa-cross' instead of 'libc6-hppa-dcv1'
Note, selecting 'libc6-m68k-cross' instead of 'libc6-m68k-dcv1'
Note, selecting 'libc6-mips-cross' instead of 'libc6-mips-dcv1'
Note, selecting 'libc6-mips32-mips64-cross' instead of 'libc6-mips32-mips64-dcv1'
Note, selecting 'libc6-mips32-mips64el-cross' instead of 'libc6-mips32-mips64el-dcv1'
Note, selecting 'libc6-mips64-cross' instead of 'libc6-mips64-dcv1'
Note, selecting 'libc6-mips64-mips-cross' instead of 'libc6-mips64-mips-dcv1'
Note, selecting 'libc6-mips64-mipsel-cross' instead of 'libc6-mips64-mipsel-dcv1'
Note, selecting 'libc6-mips64el-cross' instead of 'libc6-mips64el-dcv1'
Note, selecting 'libc6-mipsel-cross' instead of 'libc6-mipsel-dcv1'
Note, selecting 'libc6-mipsn32-mips-cross' instead of 'libc6-mipsn32-mips-dcv1'
Note, selecting 'libc6-mipsn32-mips64-cross' instead of 'libc6-mipsn32-mips64-dcv1'
Note, selecting 'libc6-mipsn32-mips64el-cross' instead of 'libc6-mipsn32-mips64el-dcv1'
Note, selecting 'libc6-mipsn32-mipsel-cross' instead of 'libc6-mipsn32-mipsel-dcv1'
Note, selecting 'libc6-powerpc-ppc64-cross' instead of 'libc6-powerpc-ppc64-dcv1'
Note, selecting 'libc6-powerpcspe-cross' instead of 'libc6-powerpcspe-dcv1'
Note, selecting 'libc6-ppc64-cross' instead of 'libc6-ppc64-dcv1'
Note, selecting 'libc6-ppc64-powerpc-cross' instead of 'libc6-ppc64-powerpc-dcv1'
Note, selecting 'libc6-s390-s390x-cross' instead of 'libc6-s390-s390x-dcv1'
Note, selecting 'libc6-s390x-cross' instead of 'libc6-s390x-dcv1'
Note, selecting 'libc6-sh4-cross' instead of 'libc6-sh4-dcv1'
Note, selecting 'libc6-sparc-sparc64-cross' instead of 'libc6-sparc-sparc64-dcv1'
Note, selecting 'libc6-sparc64-cross' instead of 'libc6-sparcv9b-sparc64-cross'
Note, selecting 'libc6-sparc64-cross' instead of 'libc6-sparc64-dcv1'
Note, selecting 'libc6.1-alpha-cross' instead of 'libc6.1-alpha-dcv1'
Note, selecting 'libc6.1-dbg-alpha-cross' instead of 'libc6.1-dbg-alpha-dcv1'
Note, selecting 'libc6.1-dev-alpha-cross' instead of 'libc6.1-dev-alpha-dcv1'
libc6 is already the newest version (2.23-0ubuntu3).
libc6-arm64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-armhf-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg is already the newest version (2.23-0ubuntu3).
libc6-dev is already the newest version (2.23-0ubuntu3).
libc6-dev-arm64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-armhf-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-powerpc-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-ppc64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-i386 is already the newest version (2.23-0ubuntu3).
libc6-powerpc-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-ppc64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-x32 is already the newest version (2.23-0ubuntu3).
libc6:i386 is already the newest version (2.23-0ubuntu3).
libc6-dev-amd64:i386 is already the newest version (2.23-0ubuntu3).
libc6-armel-armhf-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-armel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-armhf-armel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-arm64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-armel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-armhf-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-hppa-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-m68k-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-powerpc-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-powerpcspe-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-ppc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-ppc64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-s390x-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-sh4-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dbg-sparc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-armel-armhf-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-armel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-armhf-armel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-hppa-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-m68k-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips32-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips32-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips64-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips64-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mipsn32-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mipsn32-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mipsn32-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-mipsn32-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-powerpc-ppc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-powerpcspe-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-ppc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-ppc64-powerpc-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-s390-s390x-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-s390x-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-sh4-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-sparc-sparc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-dev-sparc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-hppa-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-m68k-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips32-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips32-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips64-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips64-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mipsn32-mips-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mipsn32-mips64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mipsn32-mips64el-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-mipsn32-mipsel-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-pic is already the newest version (2.23-0ubuntu3).
libc6-powerpc-ppc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-powerpcspe-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-ppc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-ppc64-powerpc-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-s390-s390x-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-s390x-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-sh4-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-sparc-sparc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6-sparc64-cross is already the newest version (2.23-0ubuntu3cross1).
libc6.1-alpha-cross is already the newest version (2.23-0ubuntu3cross1).
libc6.1-dbg-alpha-cross is already the newest version (2.23-0ubuntu3cross1).
libc6.1-dev-alpha-cross is already the newest version (2.23-0ubuntu3cross1).
The following additional packages will be installed:
  gcc-5-multilib gcc-multilib lib32asan2 lib32atomic1 lib32cilkrts5 lib32gcc-5-dev lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++6 lib32ubsan0 libx32asan2 libx32atomic1 libx32cilkrts5 libx32gcc-5-dev libx32gcc1
  libx32gomp1 libx32itm1 libx32quadmath0 libx32stdc++6 libx32ubsan0
The following NEW packages will be installed:
  gcc-5-multilib gcc-multilib lib32asan2 lib32atomic1 lib32cilkrts5 lib32gcc-5-dev lib32gomp1 lib32itm1 lib32mpx0
  lib32quadmath0 lib32stdc++6 lib32ubsan0 libc6-dev-i386 libc6-dev-x32 libx32asan2 libx32atomic1 libx32cilkrts5
  libx32gcc-5-dev libx32gcc1 libx32gomp1 libx32itm1 libx32quadmath0 libx32stdc++6 libx32ubsan0
0 to upgrade, 24 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/8,942 kB of archives.
After this operation, 37.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 303360 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Selecting previously unselected package libc6-dev-x32.
Preparing to unpack .../libc6-dev-x32_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-x32 (2.23-0ubuntu3) ...
Selecting previously unselected package libx32gcc1.
Preparing to unpack .../libx32gcc1_1%3a6.0.1-0ubuntu1_amd64.deb ...
Unpacking libx32gcc1 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package lib32gomp1.
Preparing to unpack .../lib32gomp1_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32gomp1 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32gomp1.
Preparing to unpack .../libx32gomp1_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32gomp1 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32itm1.
Preparing to unpack .../lib32itm1_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32itm1 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32itm1.
Preparing to unpack .../libx32itm1_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32itm1 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32atomic1.
Preparing to unpack .../lib32atomic1_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32atomic1 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32atomic1.
Preparing to unpack .../libx32atomic1_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32atomic1 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32asan2.
Preparing to unpack .../lib32asan2_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32asan2 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32asan2.
Preparing to unpack .../libx32asan2_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32asan2 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32stdc++6.
Preparing to unpack .../lib32stdc++6_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32stdc++6 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32ubsan0.
Preparing to unpack .../lib32ubsan0_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32ubsan0 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32stdc++6.
Preparing to unpack .../libx32stdc++6_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32stdc++6 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32ubsan0.
Preparing to unpack .../libx32ubsan0_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32ubsan0 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32cilkrts5.
Preparing to unpack .../lib32cilkrts5_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32cilkrts5 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32cilkrts5.
Preparing to unpack .../libx32cilkrts5_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32cilkrts5 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32mpx0.
Preparing to unpack .../lib32mpx0_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32mpx0 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32quadmath0.
Preparing to unpack .../lib32quadmath0_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32quadmath0 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32quadmath0.
Preparing to unpack .../libx32quadmath0_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32quadmath0 (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package lib32gcc-5-dev.
Preparing to unpack .../lib32gcc-5-dev_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking lib32gcc-5-dev (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package libx32gcc-5-dev.
Preparing to unpack .../libx32gcc-5-dev_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking libx32gcc-5-dev (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package gcc-5-multilib.
Preparing to unpack .../gcc-5-multilib_5.3.1-14ubuntu2.1_amd64.deb ...
Unpacking gcc-5-multilib (5.3.1-14ubuntu2.1) ...
Selecting previously unselected package gcc-multilib.
Preparing to unpack .../gcc-multilib_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking gcc-multilib (4:5.3.1-1ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, then I have a broken system
```

jafar@neltharion:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
23 not fully installed or removed.
Need to get 0 B/1,265 kB of archives.
After this operation, 6,940 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 303543 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
jafar@neltharion:~$ sudo apt update


Hit:1 http://au.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://au.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                  
Hit:3 http://au.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                        
Hit:5 http://apt.insynchq.com/ubuntu xenial InRelease                                                               
Hit:6 http://security.ubuntu.com/ubuntu xenial-security InRelease                                                   
Hit:7 http://archive.canonical.com/ubuntu xenial InRelease                                     
Hit:8 http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu xenial InRelease      
Hit:9 http://dl.google.com/linux/chrome/deb stable Release               
Hit:11 http://ppa.launchpad.net/numix/ppa/ubuntu xenial InRelease
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
jafar@neltharion:~$ 
jafar@neltharion:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
                  Depends: libc6-dev-x32 (>= 2.11) but it is not installed
E: Unmet dependencies. Try using -f.
jafar@neltharion:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  gcc-multilib libc6-dev-i386 libc6-dev-x32
The following NEW packages will be installed:
  gcc-multilib libc6-dev-i386 libc6-dev-x32
0 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
21 not fully installed or removed.
Need to get 0 B/2,829 kB of archives.
After this operation, 15.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 303492 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu3
Selecting previously unselected package libc6-dev-x32.
Preparing to unpack .../libc6-dev-x32_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev-x32 (2.23-0ubuntu3) ...
Selecting previously unselected package gcc-multilib.
Preparing to unpack .../gcc-multilib_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking gcc-multilib (4:5.3.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can fix my system to be able to install things again with sudo apt remove libc6-dev-i386 libc6-dev-x32 gcc-5-multilib gcc-multilib (I've done some searching) but it still leaves steam with the same problem.
How can I fix steam without resorting to a full reinstall of Ubuntu?

---

### Post by oldrocker99 on 2016-06-13
The only guaranteed way to install Steam in 16.04 is```
sudo apt-get install steam
```

Is that what you did in the first place?

---

### Post by rbfx4x on 2016-06-13
> **oldrocker99 said:**
> The only guaranteed way to install Steam in 16.04 is```
sudo apt-get install steam
```

Is that what you did in the first place?

Yes. I've also tried removing and reinstalling steam.

---

### Post by mastablasta on 2016-06-15
> Error: Couldn't find bootstrap, it's not safe to reset Steam. *[SIZE=3]**Please contact technical support.**[/SIZE]*

well, i usually follow the advice in these cases...

---

### Post by MikeCyber on 2016-06-16
Remove the hidden .steam in your home and try again.

---

