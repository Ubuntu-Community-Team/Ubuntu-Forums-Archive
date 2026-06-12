---
title: "Cupsddk"
date: 2006-09-24
forum: Desktop Environments
---

### Post by i386DX on 2006-09-24
I want to install Cupsddk. It's not in the repositories, so i downloaded the lastest [source (1.0.1)](http://www.cups.org/ddk/software.php?VERSION=1.0.1&FILE=cupsddk/1.0.1/cupsddk-1.0.1-source.tar.bz2). 

But I can't compile it:

Output of configure:
```

checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... /usr/bin/ar
checking for cp... /bin/cp
checking for htmldoc... no
checking for mkdir... /bin/mkdir
checking for nroff... /usr/bin/nroff
checking for rm... /bin/rm
checking for an ANSI C-conforming const... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether char is unsigned... no
checking for ANSI C header files... (cached) yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strlcat... no
checking for strlcpy... no
checking for strncasecmp... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for random... yes
checking for mrand48... yes
checking for lrand48... yes
checking for library containing pow... -lm
checking for cups-config... /usr/bin/cups-config
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking for fltk-config... no
checking if libsupc++ is required... yes
checking if GCC supports -fno-rtti... yes
checking if GCC supports -fno-exceptions... yes
configure: creating ./config.status
config.status: creating Makedefs
config.status: creating cupsddk.list
config.status: creating config.h
config.status: config.h is unchanged

```

then make
```

for dir in espmsg cups ppdc data examples man po; do \
                (cd $dir ; make ) || exit 1;\
        done
make[1]: Map '/home/lionel/Downloads/cupsddk-1.0.1/espmsg' wordt binnengegaan
make[1]: Er is niets te doen voor 'all'.
make[1]: Map '/home/lionel/Downloads/cupsddk-1.0.1/espmsg' wordt verlaten
make[1]: Map '/home/lionel/Downloads/cupsddk-1.0.1/cups' wordt binnengegaan
gcc -Wall -Wwrite-strings -O -fno-exceptions   -fno-rtti -o cupsprofile cupsprofile.o -lcups -L/usr/lib -lgnutls -lz -lpthread -lm -lcrypt -lm  -lsupc++
cupsprofile.o: In function `main':cupsprofile.c:(.text+0x114): undefined reference to `cups_strlcat'
:cupsprofile.c:(.text+0x128): undefined reference to `cups_strlcat'
:cupsprofile.c:(.text+0x14f): undefined reference to `cups_strlcat'
:cupsprofile.c:(.text+0x169): undefined reference to `cups_strlcat'
:cupsprofile.c:(.text+0x19d): undefined reference to `cups_strlcat'
cupsprofile.o:cupsprofile.c:(.text+0x1c0): more undefined references to `cups_strlcat' follow
cupsprofile.o: In function `main':cupsprofile.c:(.text+0x257): undefined reference to `cups_strlcpy'
collect2: ld gaf exit-status 1 terug
make[1]: *** [cupsprofile] Fout 1
make[1]: Map '/home/lionel/Downloads/cupsddk-1.0.1/cups' wordt verlaten
make: *** [all] Fout 1

```

---

### Post by whizbaby on 2006-09-24
Your ./configure says it's not there
> 
checking for strlcat... no
checking for strlcpy... no

Do you have the right cups-version and it's headers installed?
Check this
[http://www.cups.org/ddk/cupsddk.html#2_3_1](http://www.cups.org/ddk/cupsddk.html#2_3_1)

---

### Post by i386DX on 2006-09-24
I'm using the lastest version of Cups (> 1.1.19). As far as I know I installed all the headers also.

---

### Post by whizbaby on 2006-09-24
Do you have *build-essential* and linux-headers installed,too?
(BTW I found this with apt-cache search cups|grep dev
libgnomecupsui1.0-dev - UI extensions to libgnomecups (headers)
libgutenprint-dev - development files for the Gutenprint printer driver library
libgutenprintui1-dev - development files for the Gutenprint printer driver user interface library
libgutenprintui2-dev - development files for the Gutenprint printer driver user interface library
libcupsimage2-dev - Common UNIX Printing System(tm) - image development files
libcupsys2-dev - Common UNIX Printing System(tm) - development files
libgnomecups1.0-dev - GNOME library for CUPS interaction (headers)
you got most of these then?

---

### Post by dmonty on 2006-09-27
I'm having the same problems.

```

checking for strlcat... no
checking for strlcpy... no

```

I have the kernel headers installed.
The functions appear to be in:
/usr/src/linux/include/linux/string.h
/usr/include/linux/string.h
but not in
/usr/include/string.h

Maybe it is using the wrong header files?

---

