---
title: "Ophcrack."
date: 2005-12-09
forum: General Help
---

### Post by denisesballs on 2005-12-09
I thought it would be cool to check out [Ophcrack](http://ophcrack.sourceforge.net/#summary) which is a password cracker for Windows. The LiveCD runs Ubuntu, but when trying to compile it from source on my own Ubuntu I get this:

```
**jesse@jesseubuntu:~/systems/ophcrack-2.1$ ./configure**
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking for main in -lcrypto... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
**jesse@jesseubuntu:~/systems/ophcrack-2.1$ make**
make  all-recursive
make[1]: Entering directory `/home/jesse/systems/ophcrack-2.1'
Making all in src
make[2]: Entering directory `/home/jesse/systems/ophcrack-2.1/src'
gcc  -g -O2  -o ophcrack  main.o support.o interface.o callbacks.o make_redux.o make_hash.o ophcrack.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lcrypto
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libcairo.so: undefined reference to `FT_GlyphSlot_Embolden'
collect2: ld returned 1 exit status
make[2]: *** [ophcrack] Error 1
make[2]: Leaving directory `/home/jesse/systems/ophcrack-2.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jesse/systems/ophcrack-2.1'
make: *** [all-recursive-am] Error 2
**jesse@jesseubuntu:~/systems/ophcrack-2.1$**
```

Anyone have any idea for what's failing here?

---

### Post by btdown on 2005-12-09
I compiled it this morning without any troubles and have it working... Since I dont compile a whole lot, im not sure how to diagnose what you need. Do you have the 'build-essential' package installed?
 
B

---

### Post by denisesballs on 2005-12-09
[QUOTE=btdown]I compiled it this morning without any troubles and have it working... Since I dont compile a whole lot, im not sure how to diagnose what you need. Do you have the 'build-essential' package installed?
 
B[/QUOTE]

Yeah, if I didn't it wouldn't even get that far. I wonder if maybe my occasional dipping into the dapper repos may have done something?

---

### Post by denisesballs on 2005-12-10
I just installed it on my home Ubuntu box no problem. Must be something I f'ed up at the shop. Oh well!

---

### Post by btdown on 2005-12-11
I was able to make a deb package using the checkinstall option. If you PM me your email, I'll email it to you (its small) maybe it will work for you. From what i read on here..the checkinstall way of creating a deb (and sharing it) is not the most desirable, but for something you can easily remove, it doesnt seem like a bad risk.
BT

---

