---
title: "Keytouch Help"
date: 2005-12-22
forum: Desktop Environments
---

### Post by nb- on 2005-12-22
I am trying to install keytouch ( [http://keytouch.sourceforge.net/doc.html](http://keytouch.sourceforge.net/doc.html) ) for my M$ office keybaord, and while trying to make keytouch-config & keytouch-keyboard I get the following error;

```
make  all-recursive
make[1]: Entering directory `/home/lemur/keytouch-2.0/keytouch-config'
Making all in src
make[2]: Entering directory `/home/lemur/keytouch-2.0/keytouch-config/src'
source='main.c' object='main.o' libtool=no \
DEPDIR=.deps depmode=none /bin/sh ../depcomp \
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONF_DIR=\""/usr/local/etc"\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I../../mxml -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -c main.c
/bin/sh: ../depcomp: No such file or directory
make[2]: *** [main.o] Error 127
make[2]: Leaving directory `/home/lemur/keytouch-2.0/keytouch-config/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lemur/keytouch-2.0/keytouch-config'
make: *** [all] Error 2
```

Surgestions?

---

### Post by Ampersand on 2005-12-23
Firstly, make sure that you've got the dependancies listed (xlibs-dev, libgtk2-dev). Possibly try installing libtool as well.

---

### Post by nb- on 2005-12-23
Well as far as I can see all the dependencies listed are installed, I have added libtool, and there is no change, i still get the same error message.

./configure gives the following output;

```

lemur@Monkey:~/keytouch-2.0/keytouch-config$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/lemur/keytouch-2.0/keytouch-config/missing: Unknown `--run' option
Try `/home/lemur/keytouch-2.0/keytouch-config/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking dependency style of gcc... none
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking PACKAGE_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands

```

---

