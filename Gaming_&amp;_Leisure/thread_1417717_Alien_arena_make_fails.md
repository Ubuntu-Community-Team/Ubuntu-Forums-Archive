---
title: "Alien arena make fails"
date: 2010-02-27
forum: Gaming &amp; Leisure
---

### Post by HellionDarkLord on 2010-02-27
I love Alien arena, but the package in the repositories is very old.  Therefore I tried this:[URL="Guide"]http://gwos.org/doku.php
/guides:64bit:alien_arena[/URL]

Everything runs nice till the make command where this happens.

```
~/Desktop/AA/source$ make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -lpthread -O2 -fomit-frame-pointer -fexpensive-optimizations -ffast-math -march=k8"
make[1]: Entering directory `/home/gabriel/Desktop/AA/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -lpthread -O2 -fomit-frame-pointer -fexpensive-optimizations -ffast-math -march=k8 -fPIC -o release/ref_gl/gl_glx.o -c unix/gl_glx.c
unix/gl_glx.c:56:37: error: X11/extensions/Xxf86dga.h: No such file or directory
unix/gl_glx.c: In function &#8216;install_grabs&#8217;:
unix/gl_glx.c:130: error: &#8216;XF86DGADirectMouse&#8217; undeclared (first use in this function)
unix/gl_glx.c:130: error: (Each undeclared identifier is reported only once
unix/gl_glx.c:130: error: for each function it appears in.)
make[1]: *** [release/ref_gl/gl_glx.o] Error 1
make[1]: Leaving directory `/home/gabriel/Desktop/AA/source'
make: *** [build-release] Error 2

```

Is there a way to change the paths so that this will build??

Thanks for any help.

HD

---

### Post by Brebs on 2010-02-27
See [thread](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422), and its forum.

---

### Post by HellionDarkLord on 2010-02-27
I'm still not able to compile this.

```
game/acesrc/acebot_compress.c:223: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result

```

Is the first error that shows up. nothing useful for this error in Google.

Anybody have any ideas?

This error is repeated over and over again with other things.

---

