---
title: "trying to compile things, having problems"
date: 2006-01-12
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-12
I am running Ubuntu 5.10. I installed the build-essential package and I use openbox as my window manager in gnome.

I went to [http://dockapp.bensinclair.com/](http://dockapp.bensinclair.com/) and found some nice dockapps for use with openbox, but when I try compiling them I get the following error:

```

$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for X... no
configure: error: X development libraries not found
$

```

So, I cannot do a successful configure before doing make and make install.

Which package(s) am I missing for this?

---

### Post by Ampersand on 2006-01-12
xlibs-dev

---

### Post by ardchoille on 2006-02-10
Ah, that makes sense. Thank you :)

---

