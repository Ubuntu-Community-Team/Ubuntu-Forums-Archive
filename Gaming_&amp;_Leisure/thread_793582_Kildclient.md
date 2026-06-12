---
title: "Kildclient"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by Jack to Jill on 2008-05-13
jill@jill-jill:~/Desktop/kildclient-2.7.0$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

I get that when I try to configure the file for kildclient?

---

### Post by Mr A Mouse on 2008-05-13
Hmmm ... did you check config.log?

---

### Post by dfmalh on 2009-08-31
Hi, how/where do I install KildClient from the tarball?

When I run ./configer, it ends with:

```
No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'gtk+-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KILDCLIENT_CFLAGS
and KILDCLIENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```


Thanks

---

### Post by Perfect Storm on 2009-08-31
The user havn't been active since;  November 30th, 2008 and the thread is from May 14th, 2008


anyway, you need the -dev packages of the the libs you needed to compile.

---

