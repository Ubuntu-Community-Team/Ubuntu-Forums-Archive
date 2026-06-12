---
title: "Smooth GTK2 engine?"
date: 2009-02-28
forum: Desktop Environments
---

### Post by dbbolton on 2009-02-28
I have a couple themes that require a GTK2 engine called "smooth". I seem to remember seeing this engine a long time ago (like maybe on dapper). I'm on Intrepid now, and there is no such engine in the repositories. Where can I get it?

---

### Post by danillo on 2009-02-28
[http://freshmeat.net/projects/gtk-smooth-engine/](http://freshmeat.net/projects/gtk-smooth-engine/)

---

### Post by dbbolton on 2009-03-03
I tried compiling this and ran into a bunch of errors that I don't know how to interpret. First I ran:
```

./configure --prefix=/usr --enable-gtk-1

```

Here is the output of that:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... file_magic ELF [0-9][0-9]*-bit [LM]SB (shared object|dynamic lib )
checking command to parse /usr/bin/nm -B output... ok
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for file... /usr/bin/file
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for gtk-config... /usr/bin/gtk-config
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/Makefile
config.status: creating themes/Makefile
config.status: creating themes/Smooth-Funky-Monkey/Makefile
config.status: creating themes/Smooth-Funky-Monkey/gtk/Makefile
config.status: creating themes/Smooth-Funky-Monkey/gtk-2.0/Makefile
config.status: creating themes/Smooth-Okayish/Makefile
config.status: creating themes/Smooth-Okayish/gtk/Makefile
config.status: creating themes/Smooth-Okayish/gtk-2.0/Makefile
config.status: creating themes/Smooth-Peachy-Clean/Makefile
config.status: creating themes/Smooth-Peachy-Clean/gtk/Makefile
config.status: creating themes/Smooth-Peachy-Clean/gtk-2.0/Makefile
config.status: creating themes/Smooth-Sea-Ice/Makefile
config.status: creating themes/Smooth-Sea-Ice/gtk/Makefile
config.status: creating themes/Smooth-Sea-Ice/gtk-2.0/Makefile
config.status: creating themes/Smooth-Winter/Makefile
config.status: creating themes/Smooth-Winter/gtk/Makefile
config.status: creating themes/Smooth-Winter/gtk-2.0/Makefile
config.status: creating themes/Smooth-Wonderland/Makefile
config.status: creating themes/Smooth-Wonderland/gtk/Makefile
config.status: creating themes/Smooth-Wonderland/gtk-2.0/Makefile
config.status: executing depfiles commands

```


Here is the output of 'make':
```

Making all in utils
make[1]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/utils'
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT draw_gradients.lo -MD -MP -MF ".deps/draw_gradients.Tpo" \
      -c -o draw_gradients.lo `test -f 'draw_gradients.c' || echo './'`draw_gradients.c; \
    then mv ".deps/draw_gradients.Tpo" ".deps/draw_gradients.Plo"; \
    else rm -f ".deps/draw_gradients.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT draw_gradients.lo -MD -MP -MF .deps/draw_gradients.Tpo -c draw_gradients.c  -fPIC -DPIC -o draw_gradients.lo
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT draw_grips.lo -MD -MP -MF ".deps/draw_grips.Tpo" \
      -c -o draw_grips.lo `test -f 'draw_grips.c' || echo './'`draw_grips.c; \
    then mv ".deps/draw_grips.Tpo" ".deps/draw_grips.Plo"; \
    else rm -f ".deps/draw_grips.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT draw_grips.lo -MD -MP -MF .deps/draw_grips.Tpo -c draw_grips.c  -fPIC -DPIC -o draw_grips.lo
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT draw_arrows.lo -MD -MP -MF ".deps/draw_arrows.Tpo" \
      -c -o draw_arrows.lo `test -f 'draw_arrows.c' || echo './'`draw_arrows.c; \
    then mv ".deps/draw_arrows.Tpo" ".deps/draw_arrows.Plo"; \
    else rm -f ".deps/draw_arrows.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT draw_arrows.lo -MD -MP -MF .deps/draw_arrows.Tpo -c draw_arrows.c  -fPIC -DPIC -o draw_arrows.lo
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT misc_functions.lo -MD -MP -MF ".deps/misc_functions.Tpo" \
      -c -o misc_functions.lo `test -f 'misc_functions.c' || echo './'`misc_functions.c; \
    then mv ".deps/misc_functions.Tpo" ".deps/misc_functions.Plo"; \
    else rm -f ".deps/misc_functions.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT misc_functions.lo -MD -MP -MF .deps/misc_functions.Tpo -c misc_functions.c  -fPIC -DPIC -o misc_functions.lo
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT gtk1_patches.lo -MD -MP -MF ".deps/gtk1_patches.Tpo" \
      -c -o gtk1_patches.lo `test -f 'gtk1_patches.c' || echo './'`gtk1_patches.c; \
    then mv ".deps/gtk1_patches.Tpo" ".deps/gtk1_patches.Plo"; \
    else rm -f ".deps/gtk1_patches.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT gtk1_patches.lo -MD -MP -MF .deps/gtk1_patches.Tpo -c gtk1_patches.c  -fPIC -DPIC -o gtk1_patches.lo
/bin/bash ../libtool --mode=link gcc  -g -O2   -o libsmooth-utils.la  -module -avoid-version draw_gradients.lo draw_grips.lo draw_arrows.lo misc_functions.lo gtk1_patches.lo -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm 
mkdir .libs
rm -fr .libs/libsmooth-utils.la .libs/libsmooth-utils.* .libs/libsmooth-utils.*
ar cru .libs/libsmooth-utils.al draw_gradients.lo draw_grips.lo draw_arrows.lo misc_functions.lo gtk1_patches.lo
ranlib .libs/libsmooth-utils.al
creating libsmooth-utils.la
(cd .libs && rm -f libsmooth-utils.la && ln -s ../libsmooth-utils.la libsmooth-utils.la)
make[1]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/utils'
Making all in themes
make[1]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes'
Making all in Smooth-Funky-Monkey
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey'
Making all in gtk
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey/gtk'
Making all in gtk-2.0
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey/gtk-2.0'
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey'
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Funky-Monkey'
Making all in Smooth-Okayish
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish'
Making all in gtk
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish/gtk'
Making all in gtk-2.0
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish/gtk-2.0'
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish'
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Okayish'
Making all in Smooth-Peachy-Clean
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean'
Making all in gtk
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean/gtk'
Making all in gtk-2.0
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean/gtk-2.0'
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean'
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Peachy-Clean'
Making all in Smooth-Sea-Ice
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice'
Making all in gtk
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice/gtk'
Making all in gtk-2.0
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice/gtk-2.0'
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice'
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Sea-Ice'
Making all in Smooth-Winter
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter'
Making all in gtk
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter/gtk'
Making all in gtk-2.0
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter/gtk-2.0'
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter'
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Winter'
Making all in Smooth-Wonderland
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland'
Making all in gtk
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland/gtk'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland/gtk'
Making all in gtk-2.0
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland/gtk-2.0'
make[3]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland'
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes/Smooth-Wonderland'
make[2]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes'
make[1]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5/themes'
make[1]: Entering directory `/home/daniel/Source/gtk-smooth-engine-0.5'
if /bin/bash ./libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT smooth_theme_main.lo -MD -MP -MF ".deps/smooth_theme_main.Tpo" \
      -c -o smooth_theme_main.lo `test -f 'smooth_theme_main.c' || echo './'`smooth_theme_main.c; \
    then mv ".deps/smooth_theme_main.Tpo" ".deps/smooth_theme_main.Plo"; \
    else rm -f ".deps/smooth_theme_main.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT smooth_theme_main.lo -MD -MP -MF .deps/smooth_theme_main.Tpo -c smooth_theme_main.c  -fPIC -DPIC -o smooth_theme_main.lo
if /bin/bash ./libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT smooth_rc_style.lo -MD -MP -MF ".deps/smooth_rc_style.Tpo" \
      -c -o smooth_rc_style.lo `test -f 'smooth_rc_style.c' || echo './'`smooth_rc_style.c; \
    then mv ".deps/smooth_rc_style.Tpo" ".deps/smooth_rc_style.Plo"; \
    else rm -f ".deps/smooth_rc_style.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT smooth_rc_style.lo -MD -MP -MF .deps/smooth_rc_style.Tpo -c smooth_rc_style.c  -fPIC -DPIC -o smooth_rc_style.lo
if /bin/bash ./libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\"    -g -O2 -MT smooth_style.lo -MD -MP -MF ".deps/smooth_style.Tpo" \
      -c -o smooth_style.lo `test -f 'smooth_style.c' || echo './'`smooth_style.c; \
    then mv ".deps/smooth_style.Tpo" ".deps/smooth_style.Plo"; \
    else rm -f ".deps/smooth_style.Tpo"; exit 1; \
    fi
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DG_LOG_DOMAIN=\"SmoothEngine\" -g -O2 -MT smooth_style.lo -MD -MP -MF .deps/smooth_style.Tpo -c smooth_style.c  -fPIC -DPIC -o smooth_style.lo
smooth_style.c: In function 'draw_handle':
smooth_style.c:2293: error: label at end of compound statement
make[1]: *** [smooth_style.lo] Error 1
make[1]: Leaving directory `/home/daniel/Source/gtk-smooth-engine-0.5'
make: *** [all-recursive] Error 1

```

Any suggestions?

---

### Post by zoey_s on 2009-03-21
There is a workaround here; [http://ubuntuforums.org/showthread.php?t=987683&highlight=gtk+smooth](http://ubuntuforums.org/showthread.php?t=987683&highlight=gtk+smooth)

zoey

---

