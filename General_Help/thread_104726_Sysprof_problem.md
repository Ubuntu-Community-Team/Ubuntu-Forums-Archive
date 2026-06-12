---
title: "Sysprof problem"
date: 2005-12-16
forum: General Help
---

### Post by gamehack on 2005-12-16
Hi all,

As I was installing sysprof from source(no package for breezy :( ), after running configure it goes to this step:
```

gamehack@loopy:~/Desktop/sysprof-1.0$ ./configure
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 > 2.6.0 gthread-2.0 gdk-pixbuf-2.0 pangoft2 libglade-2.0... yes
checking DEP_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libglade-2.0 -I/usr/include/libxml2
checking DEP_LIBS... -pthread -lgthread-2.0 -lpangoft2-1.0 -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lz -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for cplus_demangle in -liberty... yes
checking for bfd_get_error in -lbfd... yes
*
* Sysprof requires the kernel source code to be installed.
* On a Fedora Core system the relevant package is kernel-devel
*

```

I've installed the kernel source code and it still complains...
```

gamehack@loopy:~/Desktop/sysprof-1.0$ ls /usr/src/
linux  linux-source-2.6.12.tar.bz2
gamehack@loopy:~/Desktop/sysprof-1.0$ ls /usr/src/linux
arch     Debian.src.changelog  init         Makefile       REPORTING-BUGS
cluster  Documentation         ipc          mm             scripts
COPYING  drivers               kernel       net            security
CREDITS  fs                    lib          README         sound
crypto   include               MAINTAINERS  README.Debian  usr
gamehack@loopy:~/Desktop/sysprof-1.0$

```

Anyone had luck installing sysprof on breezy?

Regards

---

