---
title: "Can't compile source"
date: 2006-07-26
forum: Desktop Environments
---

### Post by MotK on 2006-07-26
I'm trying to compile gtkpod from source bc i need video support for transferring movies.

when i run ./configure, i get the following message:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
[B]checking for PACKAGE_CFLAGS...
checking for PACKAGE_LIBS...
configure: error: *** Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found[/B]
See `config.log' for more details.

the section in bold is what concerns me. i do have libglade installed. i guessed that maybe its not installed correctly and that reinstalling might help but when i try to do that through synaptic, im alerted that its dependant on practically every package i have installed and that they would be removed as well...

anyone have any thoughts?

---

### Post by nilfilter on 2006-07-26
> **MotK said:**
>  
[...]
[B]configure: error: *** Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found[/B]
See `config.log' for more details.

the section in bold is what concerns me. i do have libglade installed. i guessed that maybe its not installed correctly and that reinstalling might help but when i try to do that through synaptic, im alerted that its dependant on practically every package i have installed and that they would be removed as well...

anyone have any thoughts?
A shot into the dark: You do have libglade2-dev installed?

---

### Post by MotK on 2006-07-26
good question. and no i dont...ive thought of that but when i try through apt-get or synaptic a box comes up telling me that libglade20-dev is something something ubuntu2 and that libglade20 is something something ubuntu1 and so it wont install...but the ubuntu1 version of libglade2.0 is the only one available to me for download...

---

### Post by Sef on 2006-07-26
> No package 'libglade-2.0' found
See `config.log' for more details.


Have you checked the config.log?

---

### Post by nilfilter on 2006-07-26
I don't have any libglade version ending with "ubuntu1" in my repos. Did you update the package information by hitting the Reload button first?

---

### Post by MotK on 2006-07-26
> **Sef said:**
> Have you checked the config.log?


yes and it says pretty much the same thing:


configure:4076: $? = 1
configure:4086: result: 
configure:4088: checking for PACKAGE_LIBS
configure:4096: $PKG_CONFIG --exists "gtk+-2.0 >= 2.4.0 gthread-2.0 >= 0.14.0 glib-2.0 > 2.4.0 libglade-2.0  >=  2.4.0 gmodule-2.0 libgpod-1.0 >= 0.3.0" >/dev/null 2>&1
configure:4099: $? = 1
configure:4109: result: 
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
configure:4118: error: *** Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
See `config.log' for more details.


and now that im at my home pc i can give you some more info about what i was trying to explain before...after reloading repos in synaptic and searching for libglade2-0 i see that the version i have is 1:2.5.1-2ubuntu1...

but when i try to install libglade2-dev, i get the following:

libglade2-dev:
  Depends: libglade2-0 (=1:2.5.1-2ubuntu1) but 1:2.5.1-2ubuntu2 is to be installed
 Depends: libxml2-dev but it is not going to be installed


so from here, i dont know what else to do...

---

### Post by MotK on 2006-07-26
okay so i figured it out. i noticed that all of my repos were looking for breezy instead of dapper. after i changed all the breezys to dapper, and reloaded everything, i was able to DL all the correct packages and gtkpod is building as we speak!

so i suppose the moral of the story, kids, is to check your repos!!!

---

