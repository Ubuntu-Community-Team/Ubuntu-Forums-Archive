---
title: "compiling kiba-plugins"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by FlexiZuu on 2007-09-02
I've compiled previous versions of kiba-plugins before but after doing an svn update i now get this error when I make.

```

make  all-recursive
make[1]: Entering directory `/home/flexizuu/kiba/trunk/kiba-plugins'
Making all in src
make[2]: Entering directory `/home/flexizuu/kiba/trunk/kiba-plugins/src'
make  all-am
make[3]: Entering directory `/home/flexizuu/kiba/trunk/kiba-plugins/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -DPNG_NO_MMX_CODE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/local/include/akamaru -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libxml2 -I/usr/include/librsvg-2 -I/usr/local/include/kiba-dock   -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0     -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include          -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -DDATADIR='"/usr/local/share"' -DLIBDIR='"/usr/local/lib"' -I../dock -I/usr/local/include    -g -O2 -MT sysinfo.lo -MD -MP -MF .deps/sysinfo.Tpo -c -o sysinfo.lo sysinfo.c
 gcc -DHAVE_CONFIG_H -I. -I.. -DPNG_NO_MMX_CODE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/local/include/akamaru -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libxml2 -I/usr/include/librsvg-2 -I/usr/local/include/kiba-dock -I/usr/include/librsvg-2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libgtop-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -I../dock -I/usr/local/include -g -O2 -MT sysinfo.lo -MD -MP -MF .deps/sysinfo.Tpo -c sysinfo.c  -fPIC -DPIC -o .libs/sysinfo.o
sysinfo.c: In function 'kiba_sysinfo_draw_surface':
sysinfo.c:446: error: 'RsvgHandle' undeclared (first use in this function)
sysinfo.c:446: error: (Each undeclared identifier is reported only once
sysinfo.c:446: error: for each function it appears in.)
sysinfo.c:446: error: 'handle' undeclared (first use in this function)
make[3]: *** [sysinfo.lo] Error 1
make[3]: Leaving directory `/home/flexizuu/kiba/trunk/kiba-plugins/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/flexizuu/kiba/trunk/kiba-plugins/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/flexizuu/kiba/trunk/kiba-plugins'
make: *** [all] Error 2
```

any ideas? btw:  I'm running 64-bit feisty on a amd64 processor.

---

