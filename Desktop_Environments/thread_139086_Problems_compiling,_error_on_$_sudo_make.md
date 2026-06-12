---
title: "Problems compiling, error on $ sudo make"
date: 2006-03-03
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-03-03
I get this error when running $ sudo make.

> 
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -MT Toggle.o -MD -MP -MF ".deps/Toggle.Tpo" \
  -c -o Toggle.o `test -f 'Toggle.c' || echo './'`Toggle.c; \
then mv -f ".deps/Toggle.Tpo" ".deps/Toggle.Po"; \
else rm -f ".deps/Toggle.Tpo"; exit 1; \
fi
rm -f libXw.a
ar cru libXw.a Base.o Box.o Button.o Field.o Label.o RootIcon.o simple.o testxw.o Toggle.o
ranlib libXw.a
gcc  -g -O2 -L/usr/X11R6/lib  -o simple  simple.o libXw.a -lpthread -ljpeg -lpng -lz  -lXext -lXmu -lXt -lX11
make[2]: Leaving directory `/home/stian/Desktop/xvidcap-1.1.4pre2/Xw'
Making all in src
make[2]: Entering directory `/home/stian/Desktop/xvidcap-1.1.4pre2/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -DVERSION=\"1.1.4\"     -g -O2 -MT xvidcap-main.o -MD -MP -MF ".deps/xvidcap-main.Tpo" \
  -c -o xvidcap-main.o `test -f 'main.c' || echo './'`main.c; \
then mv -f ".deps/xvidcap-main.Tpo" ".deps/xvidcap-main.Po"; \
else rm -f ".deps/xvidcap-main.Tpo"; exit 1; \
fi
In file included from main.c:45:
codecs.h:12:28: error: ffmpeg/avcodec.h: No such file or directory
codecs.h:13:29: error: ffmpeg/avformat.h: No such file or directory
main.c: In function &#8216;main&#8217;:
main.c:550: error: &#8216;CAP_AVI&#8217; undeclared (first use in this function)
main.c:550: error: (Each undeclared identifier is reported only once
main.c:550: error: for each function it appears in.)
make[2]: *** [xvidcap-main.o] Error 1
make[2]: Leaving directory `/home/stian/Desktop/xvidcap-1.1.4pre2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stian/Desktop/xvidcap-1.1.4pre2'
make: *** [all] Error 2


Any idea on what packages I'm missing to make a compile work?

---

### Post by jamyskis on 2006-03-03
ffmpeg (which is in repos) or probably the dev headers (which are not) by the looks of it.

---

