---
title: "wxMaxima-0.7.0a And libxml"
date: 2006-09-26
forum: Desktop Environments
---

### Post by villindesign on 2006-09-26
Hello,

I recently updated to maxima 5.10 and thought I'd also update to wxMaxima-0.7.0a. After extracting and running the command```
./configure && make
```, I get this error:
```
britt@britt-laptop:~/Desktop/wxMaxima-0.7.0a$ ./configure && make
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... found
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.6.0... yes (version 2.6.1)
checking for wxWidgets static library... no
checking if we can compile a wxWidgets program... yes
checking for xml2-config... no
checking for libxml - version >= 2.5.0... no
*** The xml2-config script installed by LIBXML could not be found
*** If libxml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
configure: error:
      xml2 must be installed on your system
      but xml2-config script couldn't be found.

      Please check that xml2-config is in path, the directory
      where xml2 libraries are installed (returned by
      'xml2-config --libs' command) is in LD_LIBRARY_PATH or
      equivalent variable and xml2 version is 2.5.0 or above.

```

I went to Synaptic to make sure libxml2 (2.6.24.dfsg-1ubuntu1) was installed, and it is. So I reinstalled, but recieved the same error. Could some one help me out? Thanks, Britt

---

### Post by croak77 on 2006-09-26
Do you have the *xxx*-dev packages installed? Example, for libxml2 you'll need libxml2-dev.

---

### Post by villindesign on 2006-09-26
No!, but now I do...thanks I got it installed. I installed the new maxima 5.10 and wxMaxima 0.7a as well as TeXmacs support of maxima 5.10. Let me know if you need help installing any of these. I got the update for TeXmacs from Andrey G. Grozin.

---

