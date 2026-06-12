---
title: "pDispora won't install"
date: 2009-04-20
forum: Gaming &amp; Leisure
---

### Post by sideaway on 2009-04-20
I'm trying to follow the little readme in the tar.gz
```

To Play: run the follow commands within this folder...
cd src
make
cd ..
./pdiaspora

```

So this is what I run

```
hamish@hamish-laptop:~/.Games$ cd ~/.Games/PDiaspora
hamish@hamish-laptop:~/.Games/PDiaspora$ cd src
hamish@hamish-laptop:~/.Games/PDiaspora/src$ make
g++ -c `sdl-config --cflags` main.c -o main.o
/bin/sh: sdl-config: not found
/bin/sh: g++: not found
make: *** [main.o] Error 127
hamish@hamish-laptop:~/.Games/PDiaspora/src$ 

```

What is wrong? what's sdl-config? how do I install g++ and sdl-config?

---

### Post by sideaway on 2009-04-20
ok, I've managed to install... well something anyway; I know have slimmed down the error messages to:
```
hamish@hamish-laptop:~/.Games/PDiaspora/src$ make
g++ -c `sdl-config --cflags` main.c -o main.o
In file included from main.c:12:
main.h:21:35: error: SDL/SDL_gfxPrimitives.h: No such file or directory
main.h:65:23: error: curl/curl.h: No such file or directory
make: *** [main.o] Error 1
```

I installed curl (sudo apt-get install curl) and but still get the error, and SDL_gfxPrimitives I just have no idea.

---

### Post by sideaway on 2009-04-20
Ok three in a row. Update SDL_gfx fixed.

```
hamish@hamish-laptop:~/.Games/PDiaspora/src$ make
g++ -c `sdl-config --cflags` main.c -o main.o
In file included from main.c:12:
main.h:65:23: error: curl/curl.h: No such file or directory
make: *** [main.o] Error 1
```

I've installed curl how come curl.h does not exist? what do i do?

---

### Post by Perfect Storm on 2009-04-20
Dud you grab the -dev of it? When compiling most of the libs needs the -dev to do so.

---

### Post by sideaway on 2009-04-20
Thankyou Articial Intelligence, I never thought of that.

I entered synatpic package manager and installed everything that looked like it had something to do with curl, it worked, but I'm sure I have about 6 packages I don't need. Hmm...

EDIT: The game works, sort of. It crashes after 30 seconds (trying to create a character) It doesn't crash at a particular point of the form rather a point in time... Can you help?

---

### Post by Perfect Storm on 2009-04-20
Been along time trying that game. What does the output of the terminal say when launcher the game from there?

---

### Post by sideaway on 2009-04-20
ok after playing around for a little while I don't think it's time based... I have no idea why/what triggers it to crash.

---

### Post by Darkcon on 2009-09-24
what i did to install pdias on ubuntu is download pdias then in this order

download SDL from [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)              - SDL itself
then download [http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)            - SDL_image
download [http://www.libsdl.org/projects/SDL_ttf/](http://www.libsdl.org/projects/SDL_ttf/)               - SDL_tff
[http://www.ferzkopp.net/joomla/content/view/19/14/](http://www.ferzkopp.net/joomla/content/view/19/14/)         -         SDL_gfx
[http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)            - curl

then went to synaptics manager, type curl into the quick search, and installed everything with the name curl in it

sudo -i to make it root terminal
extract each file you downloaded, goto each directory and
type ./configure 
then
make
then 
make install

make sure you do it for each of the files you downloaded, 

then follow the pdias readme on how to compile the game


:guitar:


see ya in game maybe

---

### Post by Bahorel on 2010-02-02
i managed to instal,l but at this point when i run ./pdiaspora it starts and after like 30 seconds it crashes. In the terminal i get :

unable to load ignore_list.txt
unable to load sos_list.txt
snt-h-1,1
rcv-h-2,nDiaspora:: 1 users
Click down at x:266 y:164
Click up at x:266 y:164
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 128 requests (127 known processed) with 9 events remaining.

after a second try i get:

*** glibc detected *** ./pdiaspora: double free or corruption (fasttop): 0x1dee1880 ***
======= Backtrace: =========
/lib/i686/cmov/libc.so.6[0xb756b824]
/lib/i686/cmov/libc.so.6[0xb756d0b3]
/lib/i686/cmov/libc.so.6(cfree+0x6d)[0xb75700ad]
/usr/lib/libSDL-1.2.so.0(SDL_DestroyMutex+0x2e)[0xb7850d3e]
/usr/lib/libSDL-1.2.so.0[0xb77fe68c]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x26)[0xb7823886]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x55)[0xb77f85b5]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e)[0xb77f863e]
/lib/i686/cmov/libc.so.6[0xb752f481]
/lib/i686/cmov/libc.so.6[0xb752f4df]
/lib/i686/cmov/libc.so.6(__libc_start_main+0xed)[0xb7516b5d]
./pdiaspora[0x8049ab1]
======= Memory map: ========
08048000-0809a000 r-xp 00000000 08:02 370166     /usr/games/pdiaspora_client-beta-1.3.2/pdiaspora_client-beta-1.3.2/pdiaspora
0809a000-0809b000 rw-p 00051000 08:02 370166     /usr/games/pdiaspora_client-beta-1.3.2/pdiaspora_client-beta-1.3.2/pdiaspora
0809b000-1ca8d000 rw-p 00000000 00:00 0 
1dec1000-1e156000 rw-p 00000000 00:00 0          [heap]
b241c000-b241d000 ---p 00000000 00:00 0 
b241d000-b2d7d000 rw-p 00000000 00:00 0 
b2d7d000-b2d7e000 ---p 00000000 00:00 0 
b2d7e000-b357e000 rw-p 00000000 00:00 0 
b357e000-b357f000 ---p 00000000 00:00 0 
b357f000-b3d7f000 rw-p 00000000 00:00 0 
b3d7f000-b3d80000 ---p 00000000 00:00 0 
b3d80000-b4580000 rw-p 00000000 00:00 0 
b4580000-b4581000 ---p 00000000 00:00 0 
b4581000-b4d81000 rw-p 00000000 00:00 0 
b4d81000-b4d82000 ---p 00000000 00:00 0 
b4d82000-b575a000 rw-p 00000000 00:00 0 
b58ae000-b5a8d000 rw-p 00000000 00:00 0 
b5b03000-b5c63000 rw-p 00000000 00:00 0 
b5c63000-b5c64000 ---p 00000000 00:00 0 
b5c64000-b6464000 rw-p 00000000 00:00 0 
b6487000-b6831000 rw-p 00000000 00:00 0 
b6a8b000-b6a90000 r-xp 00000000 08:02 563601     /lib/i686/cmov/libnss_dns-2.10.2.so
b6a90000-b6a91000 r--p 00004000 08:02 563601     /lib/i686/cmov/libnss_dns-2.10.2.so
b6a91000-b6a92000 rw-p 00005000 08:02 563601     /lib/i686/cmov/libnss_dns-2.10.2.so
b6aa0000-b6aaa000 r-xp 00000000 08:02 563591     /lib/i686/cmov/libnss_files-2.10.2.so
b6aaa000-b6aab000 r--p 00009000 08:02 563591     /lib/i686/cmov/libnss_files-2.10.2.so
b6aab000-b6aac000 rw-p 0000a000 08:02 563591     /lib/i686/cmov/libnss_files-2.10.2.so
b6aac000-b6ab5000 r-xp 00000000 08:02 563608     /lib/i686/cmov/libnss_nis-2.10.2.so
b6ab5000-b6ab6000 r--p 00008000 08:02 563608     /lib/i686/cmov/libnss_nis-2.10.2.so
b6ab6000-b6ab7000 rw-p 00009000 08:02 563608     /lib/i686/cmov/libnss_nis-2.10.2.so
b6ab7000-b6aca000 r-xp 00000000 08:02 563611     /lib/i686/cmov/libnsl-2.10.2.so
b6aca000-b6acb000 r--p 00012000 08:02 563611     /lib/i686/cmov/libnsl-2.10.2.so
b6acb000-b6acc000 rw-p 00013000 08:02 563611     /lib/i686/cmov/libnsl-2.10.2.so
b6acc000-b6ace000 rw-p 00000000 00:00 0 
b6ace000-b6ad6000 r-xp 00000000 08:02 315251     /usr/lib/libXcursor.so.1.0.2
b6ad6000-b6ad7000 rw-p 00007000 08:02 315251     /usr/lib/libXcursor.so.1.0.2
b6add000-b6ade000 rw-p 00000000 00:00 0 
b6ade000-b6ae5000 r--s 00000000 08:02 375603     /usr/lib/gconv/gconv-modules.cache
b6ae5000-b6bd3000 r--p 00144000 08:02 219917     /usr/lib/locale/locale-archive
b6bd3000-b6dd3000 r--p 00000000 08:02 219917     /usr/lib/locale/locale-archive
b6dd3000-b6dd9000 r-xp 00000000 08:02 314466     /usr/lib/libXrandr.so.2.2.0
b6dd9000-b6dda000 rw-p 00006000 08:02 314466     /usr/lib/libXrandr.so.2.2.0
b6dda000-b6de2000 r-xp 00000000 08:02 309704     /usr/lib/libXrender.so.1.3.0
b6de2000-b6de3000 rw-p 00007000 08:02 309704     /usr/lib/libXrender.so.1.3.0
b6de3000-b6df1000 r-xp 00000000 08:02 316042     /usr/lib/libXext.so.6.4.0
b6df1000-b6df2000 rw-p 0000d000 08:02 316042     /usr/lib/libXext.so.6.4.0
b6df2000-b6df6000 r-xp 00000000 08:02 312362     /usr/lib/libXdmcp.so.6.0.0
b6df6000-b6df7000 rw-p 00003000 08:02 312362     /usr/lib/libXdmcp.so.6.0.0
b6df7000-b6df9000 r-xp 00000000 08:02 309681     /usr/lib/libXau.so.6.0.0
b6df9000-b6dfa000 rw-p 00001000 08:02 309681     /usr/lib/libXau.so.6.0.0
b6dfa000-b6e12000 r-xp 00000000 08:02 314575     /usr/lib/libxcb.so.1.1.0
b6e12000-b6e13000 rw-p 00017000 08:02 314575     /usr/lib/libxcb.so.1.1.0
b6e13000-b6f2c000 r-xp 00000000 08:02 312396     /usr/lib/libX11.so.6.3.0
b6f2c000-b6f30000 rw-p 00118000 08:02 312396     /usr/lib/libX11.so.6.3.0
b6f30000-b6f33000 rw-p 00000000 00:00 0 
b6f33000-b6f36000 r-xp 00000000 08:02 314524     /usr/lib/libgpg-error.so.0.4.0
b6f36000-b6f37000 rw-p 00002000 08:02 314524     /usr/lib/libgpg-error.so.0.4.0
b6f37000-b6f46000 r-xp 00000000 08:02 312910     /usr/lib/libtasn1.so.3.1.6
b6f46000-b6f47000 rw-p 0000e000 08:02 312910     /usr/lib/libtasn1.so.3.1.6
b6f47000-b6f49000 r-xp 00000000 08:02 555693     /lib/libkeyutils-1.2.so
b6f49000-b6f4a000 rw-p 00001000 08:02 555693     /lib/libkeyutils-1.2.so
b6f4a000-b6f50000 r-xp 00000000 08:02 513697     /usr/lib/libkrb5support.so.0.1
b6f50000-b6f51000 rw-p 00005000 08:02 513697     /usr/lib/libkrb5support.so.0.1
b6f51000-b6f52000 rw-p 00000000 00:00 0 
b6f52000-b6f54000 r-xp 00000000 08:02 553863     /lib/libcom_err.so.2.1
b6f54000-b6f55000 rw-p 00001000 08:02 553863     /lib/libcom_err.so.2.1
b6f55000-b6f77000 r-xp 00000000 08:02 513699     /usr/lib/libk5crypto.so.3.1
b6f77000-b6f78000 rw-p 00022000 08:02 513699     /usr/lib/libk5crypto.so.3.1
b6f78000-b7024000 r-xp 00000000 08:02 513661     /usr/lib/libkrb5.so.3.3
b7024000-b702a000 rw-p 000ac000 08:02 513661     /usr/lib/libkrb5.so.3.3
b702a000-b7040000 r-xp 00000000 08:02 309482     /usr/lib/libsasl2.so.2.0.23
b7040000-b7041000 rw-p 00015000 08:02 309482     /usr/lib/libsasl2.so.2.0.23
b7041000-b7052000 r-xp 00000000 08:02 563613     /lib/i686/cmov/libresolv-2.10.2.so
b7052000-b7053000 r--p 00010000 08:02 563613     /lib/i686/cmov/libresolv-2.10.2.so
b7053000-b7054000 rw-p 00011000 08:02 563613     /lib/i686/cmov/libresolv-2.10.2.so
b7054000-b7057000 rw-p 00000000 00:00 0 
b7057000-b7059000 r-xp 00000000 08:02 555710     /lib/libx86.so.1
b7059000-b705a000 rw-p 00001000 08:02 555710     /lib/libx86.so.1
b705a000-b70cc000 r-xp 00000000 08:02 311651     /usr/lib/libgcrypt.so.11.5.2
b70cc000-b70cf000 rw-p 00072000 08:02 311651     /usr/lib/libgcrypt.so.11.5.2
b70cf000-b7163000 r-xp 00000000 08:02 313462     /usr/lib/libgnutls.so.26.14.12
b7163000-b7167000 rw-p 00093000 08:02 313462     /usr/lib/libgnutls.so.26.14.12
b7167000-b7194000 r-xp 00000000 08:02 309719     /usr/lib/libgssapi_krb5.so.2.2
b7194000-b7195000 rw-p 0002d000 08:02 309719     /usr/lib/libgssapi_krb5.so.2.2
b7195000-b719c000 r-xp 00000000 08:02 563595     /lib/i686/cmov/librt-2.10.2.so
b719c000-b719d000 r--p 00006000 08:02 563595     /lib/i686/cmov/librt-2.10.2.so
b719d000-b719e000 rw-p 00007000 08:02 563595     /lib/i686/cmov/librt-2.10.2.so
b719e000-b719f000 rw-p 00000000 00:00 0 
b719f000-b71e0000 r-xp 00000000 08:02 310193     /usr/lib/libldap_Abortado

i think it crashes at the point i try to write my login/name/age etc at the character creation...

i'm running squeeze Debian...
thx

---

### Post by luke_lukem on 2010-05-30
> **Darkcon said:**
>  (...)
[http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)            - libcurl

see ya in game maybe

Hi everyone, i managed to install it thanks to Darkcon, here's what i did:
From Synaptic, install th following:
libsdl-ttf2.0-dev
libsdl-ttf2.0-0
libsdl1.2-dev
libsdl1.2debian
libsdl-gfx1.2-4
libsdl-gfx1.2-dev
libsdl-image1.2
libsdl-image1.2-dev
(the -dev packages include the necessary .h files to use the libraries in make)

Then i downloaded curl from [http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)
and followed Darkcon's instructions

Then went to pdiaspora/src and typed 'make'
and voila ! it worked !

I hope it's useful :)
Cheers

---

