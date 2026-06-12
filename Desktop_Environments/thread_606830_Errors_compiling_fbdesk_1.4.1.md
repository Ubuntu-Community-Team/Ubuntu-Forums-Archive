---
title: "Errors compiling fbdesk 1.4.1"
date: 2007-11-08
forum: Desktop Environments
---

### Post by eriqjaffe on 2007-11-08
A quick bit of background:

I'm running Xubuntu 7.04 on a very, very low-end laptop (366mhz Pentium II, 128mb RAM).  Instead of using XFCE, I've opted for Fluxbox, which I'm quite happy with.  I'm trying to upgrade fbdesk to the current version (the version in the repo is 1.2.1), but I'm getting errors when I try to run make:

```
make  all-recursive
make[1]: Entering directory `/home/eriq/fbdesk-1.4.1'
Making all in src
make[2]: Entering directory `/home/eriq/fbdesk-1.4.1/src'
Making all in FbTk
make[3]: Entering directory `/home/eriq/fbdesk-1.4.1/src/FbTk'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2     -I/usr/include/libpng12  -MT Font.o -MD -MP -MF ".deps/Font.Tpo" -c -o Font.o Font.cc; \
        then mv -f ".deps/Font.Tpo" ".deps/Font.Po"; else rm -f ".deps/Font.Tpo"; exit 1; fi
In file included from /usr/include/X11/Xft/Xft.h:41,
                 from XftFontImp.hh:27,
                 from Font.cc:36:
/usr/local/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from XftFontImp.hh:27,
                 from Font.cc:36:
/usr/include/X11/Xft/Xft.h:42:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/X11/Xft/Xft.h:62: error: ‘FT_Library’ does not name a type
/usr/include/X11/Xft/Xft.h:96: error: ‘FT_UInt’ does not name a type
/usr/include/X11/Xft/Xft.h:103: error: ‘FT_UInt’ does not name a type
/usr/include/X11/Xft/Xft.h:200: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/X11/Xft/Xft.h:305: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/X11/Xft/Xft.h:363: error: ‘FT_Face’ does not name a type
/usr/include/X11/Xft/Xft.h:403: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/X11/Xft/Xft.h:409: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/X11/Xft/Xft.h:418: error: ‘FT_UInt’ has not been declared
/usr/include/X11/Xft/Xft.h:419: error: ‘FT_UInt’ has not been declared
/usr/include/X11/Xft/Xft.h:427: error: ‘FT_UInt’ does not name a type
/usr/include/X11/Xft/Xft.h:461: error: expected ‘,’ or ‘...’ before ‘*’ token
make[3]: *** [Font.o] Error 1
make[3]: Leaving directory `/home/eriq/fbdesk-1.4.1/src/FbTk'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/eriq/fbdesk-1.4.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eriq/fbdesk-1.4.1'
make: *** [all] Error 2
```

It seems pretty obvious to me that the problem has something to do with freetype or Xft (which are related, right?), but I'm not sure what, off-hand.  Any tips would be appreciated.

---

