---
title: "Compiling Ophcrack"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Twztdj on 2006-07-21
I have been trying to compile Ophcrack so I can install it on Dapper. I keep running into a "No package 'gtk+-2.0' found" error, could you tell me where I am going wrong with this? 

Terminal Output 
```
 ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
*** GTK+ 2.4 is required to build ophcrack; please make sure you have the GTK+
*** development headers installed. The latest version of GTK+ is
*** always available at http://www.gtk.org/.


```

I am somewhat linux-literate but still a newb so if you wouldnt mind explaining with a little bit of detail.

Thanks.

---

### Post by Jussi Kukkonen on 2006-07-22
Well, like it says *config.log* might give you more details. You are probably missing (at least) gtk header files. Try
```
apt-get install libgtk2.0-dev
```

---

### Post by Twztdj on 2006-07-23
I must have over looked that part in the file, cause I did read it but I thought it only listed the same error and not the libgtk2.0-dev bit. It did work though so thank you :)

---

