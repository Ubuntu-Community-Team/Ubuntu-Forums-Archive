---
title: "Problem installin themes"
date: 2005-10-05
forum: Desktop Environments
---

### Post by zac851 on 2005-10-05
I get this same error on all themes I've installed so far.  usually I open a terminal session in the directory whre I unpacked it  and then run the configure

./configure.  this is the error I get.

> hecking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether g++ supports -Wmissing-format-attribute... no
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


---

### Post by f1dave on 2005-10-05
I would look to see whether you've got gcc installed correctly in synaptic or whatever you use.

---

### Post by zac851 on 2005-10-05
Yep I HAD it all installed.  I uninstalled and then reinstalled just to make sure and I'm still get it.

---

### Post by f1dave on 2005-10-05
Sorry, on closer look i note: 

configure: error: C++ preprocessor "/lib/cpp" fails sanity check

What I actually should have said is do you have g++ installed? Thats the gnu c++ compiler.

---

### Post by zac851 on 2005-10-05
Yep, I have it installed.

---

### Post by Knome_fan on 2005-10-05
Well, according to the configure output you don't have g++ installed.

Anyway, did you install build-essential?

To additionally make sure that you got all things you need, try to install the things needed to build other KDE themes:
apt-get build-dep kde-style-lipstik

---

