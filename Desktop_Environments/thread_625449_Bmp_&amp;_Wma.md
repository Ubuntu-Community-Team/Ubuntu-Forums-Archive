---
title: "Bmp &amp; Wma"
date: 2007-11-28
forum: Desktop Environments
---

### Post by bpazolli on 2007-11-28
I'm trying to install bmp-wma and after hacking my way through the ./configure. I have hit a wall with make install or make. I get this


```
Making install in src
make[1]: Entering directory `/home/bpazolli/Desktop/bmp-wma-0.1.1/src'
Making install in libffwma
make[2]: Entering directory `/home/bpazolli/Desktop/bmp-wma-0.1.1/src/libffwma'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-allcodecs.o -MD -MP -MF ".deps/libffwma_a-allcodecs.Tpo" -c -o libffwma_a-allcodecs.o `test -f 'allcodecs.c' || echo './'`allcodecs.c; \
        then mv -f ".deps/libffwma_a-allcodecs.Tpo" ".deps/libffwma_a-allcodecs.Po"; else rm -f ".deps/libffwma_a-allcodecs.Tpo"; exit 1; fi
In file included from avcodec.h:14,
                 from allcodecs.c:21:
common.h:72: error: array type has incomplete element type
common.h:74: error: array type has incomplete element type
make[2]: *** [libffwma_a-allcodecs.o] Error 1
make[2]: Leaving directory `/home/bpazolli/Desktop/bmp-wma-0.1.1/src/libffwma'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/bpazolli/Desktop/bmp-wma-0.1.1/src'
make: *** [install-recursive] Error 1

```

Help me I am running 7.10 for AMD64

---

### Post by x64Jimbo on 2007-11-28
This thread seems to have a few people talking about a working solution:
[http://ubuntuforums.org/showthread.php?t=125562](http://ubuntuforums.org/showthread.php?t=125562)

---

### Post by bpazolli on 2007-11-28
Ok so I am doing this now

> Try following

1. Download this file

2 Open a terminal and do
Code:

sudo alien --to-deb beepmp-wma-1.0.5-1.i386.rpm

Code:

sudo dpkg -i beepmp-wma_1.0.5-2_i386.deb

Hope it helps.
__________________

I tried it before (I did see this thread before I posted) and it didn't work but now I understand I have to install alien. So I will see how that goes.

---

### Post by bpazolli on 2007-11-28
It appears to me that it doesn't like the fact that I am running AMD64

---

### Post by x64Jimbo on 2007-11-28
That could certainly have something to do with it. I have had my fair share of problems with x86_64 as well. It's not nearly as bad as it used to be, though. Have you tried other media players? Banshee is quite a robust media manager, and it seems to support all the codecs.

---

### Post by bpazolli on 2007-11-28
I've given up. Uninstalled Beep Media Player and installed some plugins now listening via rhythmbox.

---

