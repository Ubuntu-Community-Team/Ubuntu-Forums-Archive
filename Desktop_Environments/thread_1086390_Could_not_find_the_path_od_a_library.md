---
title: "Could not find the path od a library"
date: 2009-03-04
forum: Desktop Environments
---

### Post by daspriyam3 on 2009-03-04
Dear All,

 I was trying to install one package in my Ububntu Studio OS. I am new in using linux. But, There after doing: **./configure**, i got the following error:


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
./configure: line 3693: GNOME_COMPILE_WARNINGS: command not found
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 libgnomeprint-2.0 libgnomeprintui-2.0... Package libgnomeprint-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeprint-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeprint-2.0' found Package libgnomeprintui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeprintui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeprintui-2.0' found
configure: error: Library requirements (libgnomeui-2.0 libgnomeprint-2.0 libgnomeprintui-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

It was written there in the error that a few libraries was not found in pkg-config search path. but how to do that?
can anyone help me?

---

### Post by jacksaff on 2009-03-04
First, what are you trying to compile? Are there no ready built packages for it?
Second, if you have to compile whatever-it-is, then do you have all of the prerequisite packages installed? There should be a read-me that came with your download that would tell you what you need to have installed before you can compile it successfully.
Also, did you download a BSD file rather than a linux one? Might be why the libs aren't where it's expecting them to be.

---

### Post by daspriyam3 on 2009-03-05
actyally i was trying to install a package named " Ankur", through which we can write in regional language. there was a read me file. I read it and subsequently install the libraries. All these libraries are installed in my computer. But probably it could not find the path of that library. How to seta that path. In that error mesg. it although it is mentioned, but i couldn't find it.

---

