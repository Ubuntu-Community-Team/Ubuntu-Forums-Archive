---
title: "Cannot compile zsnes from source"
date: 2009-05-28
forum: Gaming &amp; Leisure
---

### Post by holamyburrito on 2009-05-28
Hi, I'm kind of a linux newb at this point, but when trying to compile zsnes from source I get the following error:

```

/zsnes_1_51/src$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=i386 -O3 -fomit-frame-pointer -s -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function ‘static int ci_char_traits::compare(const char*, const char*, size_t)’:
tools/strutil.h:34: error: ‘strncasecmp’ was not declared in this scope
make: *** [tools/strutil.o] Error 1


```

Can anyone help me understand what this means and what I can do to fix it? Thanks.

---

### Post by dfreer on 2009-05-29
Did ./configure throw up any errors? Unless Ubuntu has fixed things, you may also need to compile ZSNES using GCC 4.1. See the following thread for more info on that:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=12093](http://board.zsnes.com/phpBB2/viewtopic.php?t=12093)

---

