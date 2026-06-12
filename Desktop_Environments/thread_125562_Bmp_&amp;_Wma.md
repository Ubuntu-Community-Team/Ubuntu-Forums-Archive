---
title: "Bmp &amp; Wma"
date: 2006-02-04
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-04
I've been searching a lot on the internet to get BMP playing wma files, but none of the solutions I found works.. Is there an "easy" way to get this done?

---

### Post by cutOff on 2006-02-04
Bad research though

[http://www.ubuntuforums.org/showthread.php?t=33213&highlight=bmp+wma](http://www.ubuntuforums.org/showthread.php?t=33213&highlight=bmp+wma)

---

### Post by ESPOiG on 2006-02-04
i have got a solution... convert to mp3 :P then install xmms and there we go prob fixd

---

### Post by Ramses de Norre on 2006-02-04
I've tried the solution from that topic but I get an error on the command make

```
make  all-recursive
make[1]: Entering directory `/home/ramses/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/ramses/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/ramses/bmp-wma-0.1.1/src/libffwma'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-allcodecs.o -MD -MP -MF ".deps/libffwma_a-allcodecs.Tpo" -c -o libffwma_a-allcodecs.o `test -f 'allcodecs.c' || echo './'`allcodecs.c; \
then mv -f ".deps/libffwma_a-allcodecs.Tpo" ".deps/libffwma_a-allcodecs.Po"; else rm -f ".deps/libffwma_a-allcodecs.Tpo"; exit 1; fi
In file included from avcodec.h:14,
                 from allcodecs.c:21:
common.h:72: error: array type has incomplete element type
common.h:74: error: array type has incomplete element type
make[3]: *** [libffwma_a-allcodecs.o] Error 1
make[3]: Leaving directory `/home/ramses/bmp-wma-0.1.1/src/libffwma'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ramses/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ramses/bmp-wma-0.1.1'
make: *** [all] Error 2

```

What can I do about this?

---

### Post by Hairy_Palms on 2006-02-04
just install the bmp-wma.deb
[http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/)

then install it with 
sudo dpkg -i 	bmp-wma-0.1.1_0.1.1-1_i386.deb

---

### Post by cutOff on 2006-02-04
Try following

1. Download this [file]("http://mcmcc.bat.ru/xmms-wma/beepmp-wma-1.0.5-1.i386.rpm")

2 Open a terminal and do 
```
sudo alien --to-deb beepmp-wma-1.0.5-1.i386.rpm
```
```
sudo dpkg -i beepmp-wma_1.0.5-2_i386.deb
```

Hope it helps.

---

### Post by Ramses de Norre on 2006-02-04
Thx!:) It worked!

---

### Post by cutOff on 2006-02-04
[QUOTE=Hairy_Palms]just install the bmp-wma.deb
[http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/)

then install it with 
sudo dpkg -i 	bmp-wma-0.1.1_0.1.1-1_i386.deb[/QUOTE]
Incredible repository. Many thanks for that.

---

