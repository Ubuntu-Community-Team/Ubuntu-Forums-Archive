---
title: "X11-headers or X11-devel equivalent on Ubuntu?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by erik-the-red on 2005-11-20
I'm having some serious issues installing Enlightenment DR16.7 from source.  I believe I have all required dependencies, or at least the ones enlightenment.org requires (site is down).

However, I keep getting this error during make:

```

make  all-recursive
make[1]: Entering directory `/home/alex/enlightenment-0.16.7.1'
Making all in intl
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/intl'
Making all in dox
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/dox'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/dox'
Making all in eesh
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/eesh'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/eesh'
Making all in epp
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/epp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/epp'
Making all in src
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/src'
make[3]: Entering directory `/home/alex/enlightenment-0.16.7.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I../intl  -I/usr/local/include     -g -O2 -MT draw.o -MD -MP -MF ".deps/draw.Tpo" -c -o draw.o draw.c; \
then mv -f ".deps/draw.Tpo" ".deps/draw.Po"; else rm -f ".deps/draw.Tpo"; exit 1; fi
draw.c:1280:36: error: X11/bitmaps/flipped_gray: No such file or directory
draw.c:1281:28: error: X11/bitmaps/gray: No such file or directory
draw.c:1282:29: error: X11/bitmaps/gray3: No such file or directory
draw.c: In function ‘DrawEwinShape’:
draw.c:1358: error: ‘flipped_gray_bits’ undeclared (first use in this function)
draw.c:1358: error: (Each undeclared identifier is reported only once
draw.c:1358: error: for each function it appears in.)
draw.c:1359: error: ‘flipped_gray_width’ undeclared (first use in this function)draw.c:1359: error: ‘flipped_gray_height’ undeclared (first use in this function)
draw.c:1361: error: ‘gray_bits’ undeclared (first use in this function)
draw.c:1361: error: ‘gray_width’ undeclared (first use in this function)
draw.c:1362: error: ‘gray_height’ undeclared (first use in this function)
draw.c:1364: error: ‘gray3_bits’ undeclared (first use in this function)
draw.c:1364: error: ‘gray3_width’ undeclared (first use in this function)
draw.c:1365: error: ‘gray3_height’ undeclared (first use in this function)
make[3]: *** [draw.o] Error 1
make[3]: Leaving directory `/home/alex/enlightenment-0.16.7.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/enlightenment-0.16.7.1'
make: *** [all] Error 2

```

It seems as if I need some X11 stuff.

What is the name of X11-headers or X11-devel in Ubuntu? Maybe I can apt-get these if I know the names.

---

### Post by Alexander Kirillov on 2005-11-23
> **erik-the-red]I'm having some serious issues installing Enlightenment DR16.7 from source.  I believe I have all required dependencies, or at least the ones enlightenment.org requires (site is down).

However, I keep getting this error during make:

```

make  all-recursive
make[1]: Entering directory `/home/alex/enlightenment-0.16.7.1'
Making all in intl
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/intl'
Making all in dox
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/dox'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/dox'
Making all in eesh
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/eesh'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/eesh'
Making all in epp
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/epp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/epp'
Making all in src
make[2]: Entering directory `/home/alex/enlightenment-0.16.7.1/src'
make[3]: Entering directory `/home/alex/enlightenment-0.16.7.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I../intl  -I/usr/local/include     -g -O2 -MT draw.o -MD -MP -MF ".deps/draw.Tpo" -c -o draw.o draw.c said:**
> : *** [draw.o] Error 1
make[3]: Leaving directory `/home/alex/enlightenment-0.16.7.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/enlightenment-0.16.7.1'
make: *** [all] Error 2

```

It seems as if I need some X11 stuff.

What is the name of X11-headers or X11-devel in Ubuntu? Maybe I can apt-get these if I know the names.

try libx11-dev or -if this is not enough - meta-package 
xlibs-dev
which depends on a whole lot of x*-dev packages

---

### Post by erik-the-red on 2005-11-23
I appreciate the reply.

However, apparently, after checking aptitude, I have both libx11-dev and xlibs-dev installed!

---

### Post by doktorZee on 2006-09-16
I have the same problem compiling enlightenment.

It would be nice if it was one of the supported items on ubuntu.

---

### Post by jorgeramirez on 2006-09-29
To fix this particular problem update the "xbitmaps" package.

---

### Post by heirrookuser on 2008-05-25
The headers come with xorg-dev.  You may need to modify the makefile to point to the right directory.  They should be in /usr/include/X11

---

