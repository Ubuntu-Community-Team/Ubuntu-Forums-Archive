---
title: "Getting Duke Nukem 3d to work"
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by kleenex88h on 2006-06-02
Hey everybody!  I found a place that explains how to get Duke Nukem to work on Linux here: [http://www.icculus.org/duke3d/](http://www.icculus.org/duke3d/).  I get the source, but when I try to 'make' it, I get an error.  Actually, anytime I use the 'make' command I get an error.  I'm not sure if this is the right forum for this, but anyone have any ideas?

Thanks,
Jeremy

---

### Post by Perfect Storm on 2006-06-03
First of all, you have to show us the output from the terminal or this gonna be a long guessing contest ;)

---

### Post by jasay on 2006-06-03
[QUOTE=Artificial Intelligence]First of all, you have to show us the output from the terminal or this gonna be a long guessing contest ;)[/QUOTE]
Oh, oh me first.  I guess ```
sudo apt-get install build-essential
```What do I get if I win?

---

### Post by psyBSD on 2006-06-03
You lose, cvs version is broken.

---

### Post by bugzor on 2006-06-03
i got it compiled and installed ~3months ago after LOT OF FIXING
and it still crashed after i played ~10mins

---

### Post by kleenex88h on 2006-06-03
Artifical Inteligence - when I try to make build this is the output:

gcc -c -o build.o build.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
gcc -c -o bstub.o bstub.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
gcc -c -o engine.o engine.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
engine.c: In function ‘loadboard’:
engine.c:2974: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2975: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2976: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2977: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2980: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2981: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2982: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2983: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2984: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:2985: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3002: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3021: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3022: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3023: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3024: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3025: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3026: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3027: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
engine.c:3028: warning: pointer targets in passing argument 2 of ‘kread8’ differ in signedness
gcc -c -o cache1d.o cache1d.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
gcc -c -o sdl_driver.o sdl_driver.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
sdl_driver.c: In function ‘screencapture’:
sdl_driver.c:1548: warning: pointer targets in passing argument 3 of ‘VBE_getPalette’ differ in signedness
gcc -c -o unix_compat.o unix_compat.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
gcc -c -o a.o a.c -DUDP_NETWORKING=1  -funsigned-char -O3 -DPLATFORM_UNIX -g -Wall -I/usr/include/SDL -D_REENTRANT -fno-omit-frame-pointer -fno-strict-aliasing
a.c: In function ‘prevlineasm1’:
a.c:189: error: invalid lvalue in assignment
make: *** [a.o] Error 1



[B]
Then when I try to make duke3d (which I think is doomed since it's probably dependent on being successful with build) this is the output:[/B]




ar -fno-strict-aliasing -O2 -o animlib.o animlib.c
animlib.c: In function ‘renderframe’:
animlib.c:241: warning: pointer targets in passing argument 1 of ‘CPlayRunSkipDu mp’ differ in signedness
animlib.c:241: warning: pointer targets in passing argument 2 of ‘CPlayRunSkipDu mp’ differ in signedness
animlib.c: In function ‘ANIM_LoadAnim’:
animlib.c:277: warning: pointer targets in assignment differ in signedness
gcc -c -g -I/usr/include/SDL -D_REENTRANT -DUSE_SDL=1 -DPLATFORM_UNIX=1 -W -Wall  -Wno-unused -DUSE_EXECINFO=1 -DVOLUMEALL -DCONTROLS_CONFIG_MENU=1 -funsigned-ch ar -fno-strict-aliasing -O2 -o control.o control.c
gcc -c -g -I/usr/include/SDL -D_REENTRANT -DUSE_SDL=1 -DPLATFORM_UNIX=1 -W -Wall  -Wno-unused -DUSE_EXECINFO=1 -DVOLUMEALL -DCONTROLS_CONFIG_MENU=1 -funsigned-ch ar -fno-strict-aliasing -O2 -o config.o config.c
gcc -c -g -I/usr/include/SDL -D_REENTRANT -DUSE_SDL=1 -DPLATFORM_UNIX=1 -W -Wall  -Wno-unused -DUSE_EXECINFO=1 -DVOLUMEALL -DCONTROLS_CONFIG_MENU=1 -funsigned-ch ar -fno-strict-aliasing -O2 -o game.o game.c
game.c: In function ‘allowtimetocorrecterrorswhenquitting’:
game.c:364: warning: pointer targets in passing argument 2 of ‘sendpacket’ diffe r in signedness
game.c: In function ‘getpackets’:
game.c:403: warning: pointer targets in passing argument 2 of ‘getpacket’ differ  in signedness
game.c:513: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in  signedness
game.c: In function ‘faketimerhandler’:
game.c:797: warning: pointer targets in passing argument 2 of ‘sendpacket’ diffe r in signedness
game.c:856: warning: pointer targets in passing argument 2 of ‘sendpacket’ diffe r in signedness
game.c:866: warning: pointer targets in passing argument 2 of ‘sendpacket’ diffe r in signedness
game.c:938: warning: pointer targets in passing argument 2 of ‘sendpacket’ diffe r in signedness
game.c: In function ‘caches’:
game.c:959: warning: pointer targets in passing argument 1 of ‘sprintf’ differ i n signedness
game.c:960: warning: pointer targets in passing argument 5 of ‘printext256’ diff er in signedness
game.c:968: warning: pointer targets in passing argument 1 of ‘sprintf’ differ i n signedness
game.c:969: warning: pointer targets in passing argument 5 of ‘printext256’ diff er in signedness
game.c: In function ‘displayfragbar’:
game.c:1559: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
game.c:1560: warning: pointer targets in passing argument 3 of ‘minitext’ differ  in signedness
game.c: In function ‘coords’:
game.c:1832: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
game.c:1833: warning: pointer targets in passing argument 5 of ‘printext256’ dif fer in signedness
game.c:1834: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
game.c:1835: warning: pointer targets in passing argument 5 of ‘printext256’ dif fer in signedness
game.c:1836: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness

...yada, yada, yada...

gcc -c -g -I/usr/include/SDL -D_REENTRANT -DUSE_SDL=1 -DPLATFORM_UNIX=1 -W -Wall  -Wno-unused -DUSE_EXECINFO=1 -DVOLUMEALL -DCONTROLS_CONFIG_MENU=1 -funsigned-ch ar -fno-strict-aliasing   -c -o user.o user.c
gcc -c -g -I/usr/include/SDL -D_REENTRANT -DUSE_SDL=1 -DPLATFORM_UNIX=1 -W -Wall  -Wno-unused -DUSE_EXECINFO=1 -DVOLUMEALL -DCONTROLS_CONFIG_MENU=1 -funsigned-ch ar -fno-strict-aliasing   -c -o usrhooks.o usrhooks.c
rm -rf audiolib.a
ar rc audiolib.a fx_man.o dsl.o ll_man.o multivoc.o mv_mix.o mvreverb.o nodpmi.o  pitch.o user.o usrhooks.o
ranlib audiolib.a
make[1]: Leaving directory `/home/user/duke3d/source/audiolib'
gcc actors.o animlib.o control.o config.o game.o gamedef.o global.o keyboard.o m enues.o player.o premap.o rts.o scriplib.o sector.o sounds.o dukemusc.o audiolib /audiolib.a buildengine/cache1d.o buildengine/engine.o buildengine/sdl_driver.o buildengine/mmulti.o buildengine/pragmas.o buildengine/unix_compat.o buildengine /a.o -L/usr/lib -lSDL -lpthread -L. -lSDL -lSDL_mixer  -o duke3d
gcc: buildengine/mmulti.o: No such file or directory
gcc: buildengine/pragmas.o: No such file or directory
gcc: buildengine/a.o: No such file or directory
make: *** [duke3d] Error 1

That wasn't even the whole thing because the terminal only went back part of the way and the post length limit is 30000 characters (I had 30210), but it's not like I expect anyone to read every line of this post!

I'm starting to think this may be beyond my abilities.

---

### Post by Perfect Storm on 2006-06-03
Can I get the ./configure output (If it's using it).

---

### Post by kleenex88h on 2006-06-03
[QUOTE=Artificial Intelligence]Can I get the ./configure output (If it's using it).[/QUOTE]

It's not using it.

---

### Post by Gnobody on 2006-06-03
[LEFT]I'd try DOSbox, none of the build engine ports work for me.  DOSbox may be a little slow, or not work at all, I haven't tried it yet.
[/LEFT]

---

### Post by kleenex88h on 2006-06-03
[QUOTE=Gnobody][LEFT]I'd try DOSbox, none of the build engine ports work for me.  DOSbox may be a little slow, or not work at all, I haven't tried it yet.
[/LEFT][/QUOTE]

I did try DOSbox, and it is slow.  The draw for me to use the source is that it would then run natively on linux.

---

### Post by DoktorSeven on 2006-06-03
Whew.  I got Duke3d working but it wasn't easy.  JonoF has a modified build that works better.

I'll *try* to document the steps I took, but if I miss something, or screw up a step, I apologize... **warning: long and complicated instructions follow:**

Grab the build engine source [here](http://jonof.edgenetwork.org/index.php?p=downloads&cat=0) (JFBuild source code 20051009 596.43 kB), and the Duke3d source [here](http://jonof.edgenetwork.org/index.php?p=downloads&cat=1).  Extract both from the same directory so that you have both "jfbuild_src_20051009" and "jfduke3d_src_20051009" directories in the same place.  

Then link the build directory to "build" (from the directory you have both these subdirs in, do **ln -s jfbuild_src_20051009 build** --this is because the jfduke3dsrc expects jfbuild to be in a directory called simply "build".)

You'll need several -dev libraries (libsdl1.2-dev, I'm sure, and possibly others -- I already had several game-related development libraries installed, so I'm not sure what all it needs).  In addition, you'll need the **nasm** assembler (sudo apt-get install nasm), and fmod...

I didn't see fmod in the repositories, so I went to [the site](http://www.fmod.org/), grabbed the "FMOD 3.75 Programmers API" (fmodapi375linux.tar.gz).  Extracted it and found it had to be manually installed... *grr*.  After extract, **cd fmodapi375linux/api** then **sudo cp libfmod-3.75.so /usr/lib/** and **sudo cp inc/* /usr/include/**, and finally **sudo ln -s /usr/lib/libfmod-3.75.so /usr/lib/libfmod.so**.

Next: sound patches for Build and Duke Nukem.  (Yeah, I know, it's a lot.)  Save [this link](http://www.mephisto.ma.cx/mephisto/patches/jfbuild_src_20051009.patch) into the jfbuild_src_20051009 directory, and [this link](http://www.mephisto.ma.cx/mephisto/patches/jfduke3d_src_20051009.patch) into the jfduke3d_src_20051009 directory.  (These patches are from [this thread](http://jonof.edgenetwork.org/forum/viewtopic.php?t=580) on JonoF's messageboard.)  

Now we finally start building.  **cd jfbuild_src_20051009** and do the patch: **patch -p1 < jfbuild_src_20051009.patch**.  Then just type **make**.  Any errors, look for what it's trying to find (particularly in lines saying they can't find a .h file) and install the appropriate -dev package.

When done, **cd ../jfduke3d_src_20051009**, patch it with **patch -p1 < jfduke3d_src_20051009.patch**, and type **make**.

*whew*.  Copy over your duke3d.grp file from a Duke3d install or disk into the jfduke3d source directory where the **duke3d** binary now rests (**duke3d.grp** must be lowercase) and type ./duke3d to start the game.

It worked for me, anyway... sorry if it doesn't for you.

---

### Post by Or'Enn on 2006-07-28
This worked great for me. I at least have the game installed and able to run.
But..:
When I type ./duke3d it starts up in 320x240 (8-bpp windowed)!

```
addsearchpath(): Added /home/orenn/Spill/duke3d/jfduke3d_src_20051009/
addsearchpath(): Added /home/orenn/.jfduke3d/
Duke Nukem 3D v1.999
Copyright (c) 1996 3D Realms Entertainment
Compiling: GAME.CON (151190 bytes)
Including: DEFS.CON (35992 bytes)
Including: USER.CON (45482 bytes)
Looks like Atomic Edition CON files.
Code Size: 64824 bytes (1795 labels).
Initialising SDL system interface (compiled with SDL version 1.2.9, DLL version 1.2.9)
Loading libGL.so
**Xlib:  extension "XFree86-DRI" missing on display ":1.0".**
Using "x11" video driver
Detecting video modes:
  - 1280x1024 32-bit fullscreen
  - 1152x864 8-bit windowed
  - 1024x768 8-bit windowed
  - 800x600 8-bit windowed
  - 640x480 8-bit windowed
  - 640x400 8-bit windowed
  - 512x384 8-bit windowed
  - 480x360 8-bit windowed
  - 400x300 8-bit windowed
  - 320x240 8-bit windowed
  - 320x200 8-bit windowed
  - 1152x864 32-bit windowed
  - 1024x768 32-bit windowed
  - 800x600 32-bit windowed
  - 640x480 32-bit windowed
  - 640x400 32-bit windowed
  - 512x384 32-bit windowed
  - 480x360 32-bit windowed
  - 400x300 32-bit windowed
  - 320x240 32-bit windowed
  - 320x200 32-bit windowed
0 joystick(s) found
Initialising mouse
CONTROL_Startup: Mouse Present
Initialising timer
Loading art header.
initcache(): Initialised with 33554416 bytes
mmulti: This machine's IP is 127.0.0.1
RTS Manager Started.
RTS file DUKE.RTS was not found
Loading palette/lookups.
**Setting video mode 320x240 (8-bpp windowed)**
Checking music inits.
Checking sound inits.
open /dev/sequencer: No such file or directory

```
Any idea how this can be corrected? On the first run I got:
```
Failure setting video mode 640x480x8 fullscreen! Attempting safer mode...Setting video mode 320x240 (8-bpp windowed)
```

---

### Post by Daniel15 on 2006-09-20
Thanks for that tutorial, DoktorSeve! It's all working fine for me :) I did need to install some libraries (libsdl1.2-dev and  libsdl-mixer1.2, and I think libgl1-mesa-dev as well. There may be others which I've installed in the past). 

> 
When I type ./duke3d it starts up in 320x240 (8-bpp windowed)!
That happened for me as well. However, going into the options and selecting a higher resolution seems to work fine ;)

---

### Post by saladasalad on 2006-10-01
Anyone had any luck getting this to work on amd64? All I get when I try to build jfbuild_src_20051009 is this:

```

gcc -march=pentium -fomit-frame-pointer -O2 -W -Wall -Wimplicit -Wno-char-subscripts -Wno-unused -funsigned-char -fno-strict-aliasing -DNO_GCC_BUILTINS -DKSFORBUILD -Iinclude  -DRENDERTYPESDL=1 -DSUPERBUILD -DPOLYMOST -DUSE_OPENGL -DDYNAMIC_OPENGL -I/usr/include/SDL -D_REENTRANT -DHAVE_GTK2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -c src/game.c -o obj.gnu/game.o 2>&1
src/game.c:1: error: CPU you selected does not support x86-64 instruction set
src/game.c:1: error: CPU you selected does not support x86-64 instruction set
make: *** [obj.gnu/game.o] Error 1

```

Editing the Makefile and adding march=athlon64, gives this:

```

In file included from src/game.c:10:
include/pragmas.h:3699:2: error: #error Unsupported compiler or architecture.
src/game.c: In function &#8216;prepareboard&#8217;:
src/game.c:1139: warning: implicit declaration of function &#8216;clearbufbyte&#8217;
src/game.c:1349: warning: implicit declaration of function &#8216;klabs&#8217;
src/game.c:1475: warning: implicit declaration of function &#8216;mulscale7&#8217;
src/game.c:1477: warning: implicit declaration of function &#8216;mulscale5&#8217;
src/game.c:1493: warning: implicit declaration of function &#8216;copybuf&#8217;
src/game.c:1504: warning: implicit declaration of function &#8216;scale&#8217;
src/game.c: In function &#8216;checktouchsprite&#8217;:
src/game.c:1561: warning: implicit declaration of function &#8216;mulscale4&#8217;
src/game.c:1562: warning: implicit declaration of function &#8216;mulscale8&#8217;
src/game.c: In function &#8216;analyzesprites&#8217;:
src/game.c:1905: warning: implicit declaration of function &#8216;mulscale16&#8217;
src/game.c: In function &#8216;statuslistcode&#8217;:
src/game.c:2513: warning: implicit declaration of function &#8216;sqr&#8217;
src/game.c:2546: warning: implicit declaration of function &#8216;divscale7&#8217;
src/game.c:2550: warning: implicit declaration of function &#8216;divscale9&#8217;
src/game.c:2564: warning: implicit declaration of function &#8216;mulscale22&#8217;
src/game.c:2597: warning: implicit declaration of function &#8216;mulscale30&#8217;
src/game.c:2599: warning: implicit declaration of function &#8216;ksgn&#8217;
src/game.c:2615: warning: implicit declaration of function &#8216;mulscale14&#8217;
src/game.c:2623: warning: implicit declaration of function &#8216;divscale17&#8217;
src/game.c:2626: warning: implicit declaration of function &#8216;mulscale12&#8217;
src/game.c:2643: warning: implicit declaration of function &#8216;mulscale13&#8217;
src/game.c:2649: warning: implicit declaration of function &#8216;dmulscale14&#8217;
src/game.c: In function &#8216;view&#8217;:
src/game.c:3506: warning: implicit declaration of function &#8216;mulscale28&#8217;
src/game.c:3514: warning: implicit declaration of function &#8216;divscale16&#8217;
src/game.c: In function &#8216;drawscreen&#8217;:
src/game.c:3693: warning: implicit declaration of function &#8216;dmulscale12&#8217;
src/game.c: In function &#8216;movethings&#8217;:
src/game.c:4196: warning: implicit declaration of function &#8216;copybufbyte&#8217;
src/game.c:4949:2: error: #error Unsupported compiler or architecture
src/game.c: In function &#8216;movelava&#8217;:
src/game.c:5019: warning: implicit declaration of function &#8216;addlava&#8217;
src/game.c: In function &#8216;drawoverheadmap&#8217;:
src/game.c:5824: warning: implicit declaration of function &#8216;dmulscale16&#8217;
make: *** [obj.gnu/game.o] Error 1

```

Any ideas?

---

### Post by jdunn on 2006-10-01
Bah!  Just wait for Duke Nukem' Forever...and ever and ever and ever and ever.......

I hear some stores allow you to pre-order the game...for when hell freezes over.

---

### Post by Zaggy on 2006-10-17
fixed the dependency, will provide ready to run duke3d without licensed files

---

### Post by kvonb on 2006-10-19
Hey zaggy, I would like a copy of that when you get it done.

Regards,  Kev :)

---

### Post by nonocake on 2006-11-04
Hi Zaggy id like a copy of it too

---

### Post by rutger83 on 2006-11-06
> **saladasalad said:**
> Anyone had any luck getting this to work on amd64? 
Any ideas?

For getting it to work on AMD64, you should probably try this:

edit the Makefile to change the CFLAGS variable. Instead of -march=pentium, make it -march=athlon64 -m32

```

CFLAGS=-march=athlon64 -m32 $(debug)

```

The only problem is that you now have to link to several 32-bit libraries, so you'd better install them in /usr/lib32 or whereever you like. If you add the 32 bit libraries from some uncommon place, you'd better adjust the LIBS variable to make it say:

```

LIBS=-L/your/lib32/directory/

```

I have tested the compiling, that works, but I don't have time to find the libs (yet). Hope to have helped someone...

---

### Post by rutger83 on 2006-11-07
Ok, I've got it working on my AMD64 dapper drake. Here's what I did:

I edited the Makefiles and adjusted these values:
```

CFLAGS=-march=athlon64 -m32 $(debug)
LIBS=-L/your/lib32/directory/

```

In the lfduke directory there is something in the LIBS variable that must be appended to the value I gave here. Then I had to search for the correct libraries. I already had a few, and I have a edgy i386 version on this pc, so I could combine those. Then before running, if you don't want to install the libs in your /usr/lib32 directory, you have to adjust your LD_LIBRARY_PATH variable to include your win32 libs (in terminal):

```

export LD_LIBRARY=$LD_LIBRARY_PATH:/your/lib32/directory

```


Happy Duking! :D :D :D 


The libs that I needed were:
libatk-1.0.so
libatk-1.0.so.0.1114.0
libcairo.so
libcairo.so.2.2.4
libc.so
libdl.a
libdl.so
libexpat.so.0
libexpat.so.1
libexpat.so.1.0.0
libfmod-3.75.so
libfontconfig.so
libfontconfig.so.1.0.4
libfreetype.so
libfreetype.so.6
libfreetype.so.6.3.8
libgcc_s.so.1
libgdk_pixbuf-2.0.so
libgdk_pixbuf-2.0.so.0.800.20
libgdk-x11-2.0.so
libgdk-x11-2.0.so.0.800.20
libglib-2.0.so
libglib-2.0.so.0.1000.3
libGL.so
libGL.so.1
libGL.so.1.2
libGLU.so.1
libGLU.so.1.3.060401
libgmodule-2.0.so
libgmodule-2.0.so.0.1000.3
libgobject-2.0.so
libgobject-2.0.so.0.1000.3
libgtk-x11-2.0.so
libgtk-x11-2.0.so.0.800.20
libm.a
libm.so
libogg.so.0
libogg.so.0.5.2
libpango-1.0.so
libpango-1.0.so.0.1201.2
libpangocairo-1.0.so
libpangocairo-1.0.so.0.1201.2
libpangoft2-1.0.so.0
libpangoft2-1.0.so.0.1201.2
libpng12.so.0
libpng12.so.0.1.2.8
libpthread-2.3.6.so
libpthread.a
libpthread.so
libpthread.so.0
libsasl2.so.2.0.19
libSDL-1.2.so.0.7.1
libSDL_mixer-1.2.so.0
libSDL_mixer-1.2.so.0.2.4
libSDL_mixer.so
libSDL.so
libsmpeg-0.4.so.0
libsmpeg-0.4.so.0.1.4
libstdc++.so.6
libstdc++.so.6.0.7
libvorbisfile.so
libvorbisfile.so.3
libvorbisfile.so.3.1.1
libvorbis.so.0
libvorbis.so.0.3.0
libX11.so
libX11.so.6
libX11.so.6.2.0
libXau.so.6
libXau.so.6.0.0
libXcursor.so
libXcursor.so.1.0.2
libXext.so
libXext.so.6
libXext.so.6.4.0
libXfixes.so
libXfixes.so.3.0.0
libXinerama.so
libXinerama.so.1.0.0
libXi.so
libXi.so.6.0.0
libXrandr.so
libXrandr.so.2.0.0
libXrender.so
libXrender.so.1.3.0
libz.so.1
libz.so.1.2.3
list.txt

---

### Post by CowzRule on 2006-11-07
Have you guys seen this?? [http://hrp.duke4.net/index.php]("http://hrp.duke4.net/index.php")

---

### Post by dannyboy79 on 2006-11-07
> **CowzRule said:**
> Have you guys seen this?? [http://hrp.duke4.net/index.php]("http://hrp.duke4.net/index.php")

well have you actually tried it? does it work, what are your specs? Dapper or Edgy?

you do realize that you have to have the game installed before applying this High Resolution Pack. Again, the link is only for a resolution pack, not the game!

---

### Post by CowzRule on 2006-11-08
> **dannyboy79 said:**
> well have you actually tried it? does it work, what are your specs? Dapper or Edgy?
you do realize that you have to have the game installed before applying this High Resolution Pack. Again, the link is only for a resolution pack, not the game!
I'm running Edgy now and haven't tried it yet, but I did get it working in Dapper. I used the instuctions from [here]("http://hrp.duke4.net/wiki/doku.php?id=documentation:installing_running_the_hrp_and_ports#linux_installation"). I basically only installed it, played a couple levels then went on to trying other stuff as I am new to Linux so I can't really say how stable it would be.
The HRP download comes with everything you need to run Duke except the Duke3d.grp file from the original Duke3d or Atomic Edition. It has both Eduke32 and JonoF ports.
As far as my specs, they were; Ubuntu Dapper Drake, Athlon XP 3200+, 1 gig pc3200, Ati X800Pro with ATI's proprietary FGLRX drivers (8.29.6).

---

### Post by rutger83 on 2006-11-08
> **dannyboy79 said:**
> well have you actually tried it? does it work, what are your specs? Dapper or Edgy?

you do realize that you have to have the game installed before applying this High Resolution Pack. Again, the link is only for a resolution pack, not the game!

You are right that this is only the resolution pack, but CowzRule is right that this is a nice link. You can start JonoF's duke to use the HRP. Just start it with 

```

./duke3d /gduke3d_xtr.zip

```

(where you add the name of the hrp directly after the /g). You can also add other extensions the same way, just make sure you have the packs in the right directory.


Note about the AMD64 version, I didn't get the OpenGL lib support yet, but the game runs perfectly. But the HRP doesn't work without OpenGL.

Edit:
I also have Edgy x86 here, and there the HRP works flawless! Only thing that doesn't work on linux is midi support (win-only), so no nice duke tunes, but there are worse things I guess...
My specs: Athlon64 3200+, Ati xPress200M (on board), fglrx 8.26.x, 1 GB pc3200

---

### Post by dannyboy79 on 2006-11-08
ok, i didn't say it was a nice link! I was merely pointing out that not the game. so are you saying that I am suppose to follow the instructions to install 3dduke from the 1 page of this thread, then do the hrp thing? Also, Cowzrule states, "The HRP download comes with everything you need to run Duke except the Duke3d.grp file from the original Duke3d or Atomic Edition." So where do I get the Duke3d.grp from????

---

### Post by rutger83 on 2006-11-08
> **dannyboy79 said:**
> ok, i didn't say it was a nice link! I was merely pointing out that not the game. so are you saying that I am suppose to follow the instructions to install 3dduke from the 1 page of this thread, then do the hrp thing? Also, Cowzrule states, "The HRP download comes with everything you need to run Duke except the Duke3d.grp file from the original Duke3d or Atomic Edition." So where do I get the Duke3d.grp from????

You *cannot* run this version of Duke Nukem without having the original game! In the original game (shareware, atomic, whatever) there is a file called DUKE3D.GRP. You need that one (but make it lowercase). Further, I don't think that link has everything, I still needed the JonoF port, but maybe because I can't run x86 anyway. Anyway, I don't bother to look :), the JonoF port works fine, and it's not thát hard :).

Further, I am starting to port the JonoF port to use fmodex (next version: 4). Fmod 3.75 is only distributed binary and doesn't come (and probably never will) for x86-64 platforms. With fmodex 4.04 it will then natively run on AMD64, so we can compile DN3D on all linux versions WITH MIDI and openGL support! Before we had to do without music, but this seems like a nice project for me to work on 8). I will you know when it's done on this page.

---

### Post by CowzRule on 2006-11-08
> **dannyboy79 said:**
> ok, i didn't say it was a nice link! I was merely pointing out that not the game. so are you saying that I am suppose to follow the instructions to install 3dduke from the 1 page of this thread, then do the hrp thing? Also, Cowzrule states, "The HRP download comes with everything you need to run Duke except the Duke3d.grp file from the original Duke3d or Atomic Edition." So where do I get the Duke3d.grp from????

I posted the link to the HRP pack becuase the new graphics are, imho, really cool and it might help with getting Duke running on your box.
When I installed it, it made links to run the game in the "Games" menu with links to run it with either Eduke32 or JFDuke and with or without the HRP stuff.

You get the Duke3d.grp file from the original game, either regular Duke3d or the Atomic Edition. I've read that the .grp file from the Atomic Edition is prefered.

One of the things I remember: The installer installs a file in both "/usr/share/games/eduke32/" and "/usr/share/games/jfduke3d/" called "duke3d.grp" Its type is "link to unknown". If you right click on it and select properties you'll see that it's looking for "/usr/share/games/buildengine/duke3d.grp". which the installer didn't create. You'll need to create that folder and then put your "duke3d.grp" file there.

---

### Post by dannyboy79 on 2006-11-08
ok, i have to ask this question again because no one seems to be answering me. When I ask, where do you get the Duke3d.grp file, I am not asking what game it comes from, I am asking where do I get the game. More specifically, is it free?

---

### Post by rutger83 on 2006-11-08
> 
You *cannot* run this version of Duke Nukem without having the original game!


So no, it's not free. Although many people can get that file from any p2p file-sharing network, usenet or whatever, they are not allowed to. ;)

---

### Post by CowzRule on 2006-11-08
> **dannyboy79 said:**
> ok, i have to ask this question again because no one seems to be answering me. When I ask, where do you get the Duke3d.grp file, I am not asking what game it comes from, I am asking where do I get the game. More specifically, is it free?

Sorry, I assumed you already had the game.

No, the game is not free and where you could buy it today I don't know.

The source code that is free is what you need to build a binary to allow you to run the game on todays computers. It still requires you to have the game and from that you only need the .grp file which has all the games data, i.e. maps, sounds, graphics, ect...

P.S. dannyboy79... I sent you a PM

---

### Post by Ben Sprinkle on 2006-11-09
Just download the regular dos version. (You can get from any pirate site, not going to post links)
Then get DosBox, find it in the repositories. Will emulate it, kind of like Wine but emulates dos.

---

### Post by pay on 2006-11-09
The Shareware version is free (as in beer) and can be downloaded from here [http://www.3drealms.com/duke3d/](http://www.3drealms.com/duke3d/)
It contains the Duke3d.grp file.

---

### Post by Ben Sprinkle on 2006-11-10
Not the full one.

---

### Post by rutger83 on 2006-11-10
For dosbox: sn't it more fun to have it running natively? Fullscreen, native opengl support, hrp, etc...

---

### Post by Ben Sprinkle on 2006-11-13
First time I saw HRP blew my mind. :)

---

### Post by po0f on 2006-11-15
DoktorSeven,

I just want to let you know that those instructions worked flawlessly for me, you should consider writing a set-by-step HOWTO and reposting it.

I can now kick *** and chew bubble gum at the same time.  :)

---

### Post by BrendanM on 2007-01-28
Hey all, I just got this working and it's awesome. I was able to just install the packages available on the HRP website, and it does install the full game (both eDuke and JFDuke) minus the Duke3d.grp file. I have a couple questions though. First, I used the .grp file from the shareware version and it says stuff like "Unregistered Version" on it. Does using this shareware .grp have any impact on the actual gameplay, or does it just add a nag screen? Second, there doesn't seem to be any music in the game. Is that because midi is closed-source? Is there anything I can do to fix that?

---

### Post by yarg on 2007-04-22
Seems I am a bit late to this party.. :) I got JonoF's source to compile by following DoktorSeven's instructions. The only other dependency I needed was libsdl-mixer1.2-dev, which was quickly found in the repository. However, now there seems to be a problem with ALSA, which is preventing me from running the binary.

```

...
0 joystick(s) found
Initialising mouse
CONTROL_Startup: Mouse Present
Initialising timer
Loading art header.
initcache(): Initialised with 33554416 bytes
mmulti: This machine's IP is *xxx.xx.xx.xxx*
RTS Manager Started.
RTS file DUKE.RTS was not found
Loading palette/lookups.
Setting video mode 320x240 (8-bpp windowed)
Checking music inits.
Checking sound inits.
[B]ALSA lib pcm.c:6650:(snd_pcm_slave_conf) Unknown field fragment_size
Sound startup error: Unknown Multivoc error code.[/B]

```
Any ideas on where to start? I'm running Edgy (Gnome) with 2.6.17-11-386 kernel.

**Update**: I should have investigated ALSA's configs a little more before posting. I commented out the line "fragment_size 4096" in the /etc/asound.conf file, and it now runs.. with sound (until I start a new game). When I start a game, sound ceases to work, and the program must be killed from the console to exit.

---

### Post by Mblackwell on 2007-04-22
[http://wiki.eduke32.com/stuff/](http://wiki.eduke32.com/stuff/)

There's a Linux binary snapshot from the 14th (file upload dated the 15th). I know the guy making the port, good stuff (I do beta testing). There's also an SVN but it's not public so it's the best you can get for now ;).

[www.eduke32.com](www.eduke32.com) info on Eduke32.

It runs Duke Nukem 3D, as well as mods and NAM/WWII GI. It also extends modding capabilities and has some graphical updates even beyond what Jonof's port has. Newer versions of the HRP are based off of Eduke32.

As of that snapshot everything should work swimmingly on Ubuntu.

---

### Post by yarg on 2007-04-22
> As of that snapshot everything should work swimmingly on Ubuntu.

Hmm, pre-compiled binary Segfaults for me. :(

I was able to get the latest snapshot to compile for linux though. It runs. Unfortunately, no linux sound support? The source has been out for awhile.. I'm surprised nobody's got sound working yet. The graphics are definitely smooth, and I haven't even finished getting the HRP to try yet.

---

### Post by Mblackwell on 2007-04-22
The sound is working in that precompiled snapshot. It's not in the source for various reasons. It's on the private SVN though (not that that helps you).

What are you running though so I can give a bug report to the guy making it and see if he has an idea of why it would.

---

### Post by guysmiley25 on 2007-05-28
I got Duke Nukem working yay!

I was wondering if there was a nice way to install this into your system, or a way to create a nice way to install. eg a .deb package.

Where you have like duke3d in /usr/games/duke3d, etc.

Thanks

---

### Post by guysmiley25 on 2007-05-29
I have found that all you need after the compile, is the duke3d binary file, and the duke3d.grp file.

So I deleted everything else, And remove all the packages/libs that I had installed during the complie. Then when I then ran duke3d, It complained about libSDL Mixer. So I installed libsdl-mixer1.2. And now all works well.

I have ever done anything like this before but I was wondering would it not be possible to have the setup laid out like this

    1) Have a directory /usr/lib/games/jfduke3d
    2) In this directory a script jfduke3d, and the duke3d binary
    3) link (ln -s) jfduke3d to /usr/share/games/duke3d

And have the jfduke3d script be kinda like so
```

if [ /usr/lib/games/jfduke3d/duke.grp exist ] ; then
    /usr/lib/games/duke3d
else
    echo jfduke3d not configured
    echo Please run as root, duke3d -setup
fi

if [ $1 == "-setup" ] ; then
    Take user though putting in there CD and copy over there duke.grp file.
fi

```
Or something.

And then package all this into a .deb file, and make it have dependences libsdl-mixer1.2 and what ever else is required.

Would this work? as it would be a much nicer way to install.

---

### Post by Mochtroid-X on 2007-07-20
This place has .deb installers for eDuke32 and JFDuke3D, though I cannot get eDuke32 to work or JFDuke3D to run in 3D (or at a playable speed for that matter), but here it is:

[http://ny00123.sitesled.com/files.html](http://ny00123.sitesled.com/files.html)

---

### Post by the_eternal_dark on 2007-07-20
Mochtroid-X, I'm having the same problems. Sometimes it won't even start.

The high resolution pack is available too. [http://hrp.duke4.net/download.php](http://hrp.duke4.net/download.php)

Anyone care to give a walkthrough? Maybe we are missing something....

---

### Post by Mochtroid-X on 2007-07-28
Well, just messing around today I clicked on the jfduke3d launcher in games and, amazingly, it runs at playable speed. It still only runs in 8-bit software rendering, but I can play it though.

-edit-
I got it running in 32-bit OpenGL rendering! I noticed the .jfduke3d folder in my home folder had a log file in it for duke3d. Inside I found a line saying:

```
Loading libGL.so
Failed loading OpenGL driver. GL modes will be unavailable.
```

I searched for this file and found one in '/usr/lib/nvidia' under the filename 'libGL.so.1.2.xlibmesa'. I made a link to it in my .jfduke3d folder and renamed it to libGL.so and was able to play it in 32-bit 3D and fullscreen! :guitar:

Unfortunately... ...it lags badly... ...and I have an overclocked GeForce 7950GT... :confused:

---

### Post by atlanta800 on 2007-08-03
There is an ubuntu deb [here]("http://ny00123.sitesled.com/files.html") for JFDuke3D. You have to copy your binaries (from the CD or Windows Install) to ~/.jfduke3d/

But when I try to run it I get:
```
There was a problem initialising the Build engine:
Failed to load TABLES.DAT!
```

I searched around and found some things about renaming DUKE3D.GRP to duke3d.grp but that didn't help any. Any ideas?

EDIT: Seems like I posted too soon. The duke3d.grp and DUKE.RTS files need to go in your /usr/share/games/jfduke3d/ directory. However I still have some problems:
1) Sound works through the menu until I start a game, and then I get no sound
2) The game does not close happily it usually locks up the system (solved with a restart of X) or if it does exit, I loose control of the mouse (it just sites there, and i can't move it)
3) Most likely related to 2, any settings changes I make aren't saved when I go to reload.

Anyone have any ideas?

---

### Post by Old Pink on 2007-08-15
> **atlanta800 said:**
> There is an ubuntu deb [here]("http://ny00123.sitesled.com/files.html") for JFDuke3D. You have to copy your binaries (from the CD or Windows Install) to ~/.jfduke3d/

But when I try to run it I get:
```
There was a problem initialising the Build engine:
Failed to load TABLES.DAT!
```I searched around and found some things about renaming DUKE3D.GRP to duke3d.grp but that didn't help any. Any ideas?

EDIT: Seems like I posted too soon. The duke3d.grp and DUKE.RTS files need to go in your /usr/share/games/jfduke3d/ directory. However I still have some problems:
1) Sound works through the menu until I start a game, and then I get no sound
2) The game does not close happily it usually locks up the system (solved with a restart of X) or if it does exit, I loose control of the mouse (it just sites there, and i can't move it)
3) Most likely related to 2, any settings changes I make aren't saved when I go to reload.

Anyone have any ideas?So I need a windows version in order to get GAME.CON ?

---

### Post by Mochtroid-X on 2007-08-18
I only needed the duke3d.grp to get it working myself.

---

### Post by fululian on 2007-10-22
> **atlanta800 said:**
>  However I still have some problems:
1) Sound works through the menu until I start a game, and then I get no sound
2) The game does not close happily it usually locks up the system (solved with a restart of X) or if it does exit, I loose control of the mouse (it just sites there, and i can't move it)
3) Most likely related to 2, any settings changes I make aren't saved when I go to reload.

Anyone have any ideas?

those are exactly my problems at the moment here. has anyone resolved this in the meantime? i think this is the most viable solution for duke3d on ubuntu right now.

---

### Post by mister_k81 on 2007-10-22
> **fululian said:**
> those are exactly my problems at the moment here. has anyone resolved this in the meantime? i think this is the most viable solution for duke3d on ubuntu right now.

If you are using EDuke32 or JFDuke, did you try installing timidity from the repositories? I'm pretty sure the game is crashing, because it's trying to play the game midi music files but can't because there's no software to play them.

---

### Post by fululian on 2007-10-23
gee, this was some genius-tip, which solved everything in two seconds. thank you very much. i am now playing duke nukem 3d atomic edition  full screen at 1280 x 800, full sound, saving everything at will, and exiting correctly. let me buy you a drink next time you in berlin.

:guitar:

bye

---

### Post by Mblackwell on 2007-10-23
You should definitely be using Eduke32 instead of JFDuke if you can though, as JFDuke hasn't been updated in a long while and isn't compatible with the latest HRP, or with a lot of newer mods.

---

### Post by fululian on 2007-10-23
eduke32 wouldn't wanna work on my sys, so jfduke is the choice for me until now...but i'll try eduke32 once in a while. thanks.

another thing, since every one is talking about the "high resolution pack", i often tried to get it via [http://www.edgefiles.com/files/21980.html]("http://www.edgefiles.com/files/21980.html") , but this server seems to have been down for quite a while, and i cannot find anywhere else. does anyone know where to get this pack?

thanks.

---

### Post by beeldings on 2007-10-23
Have you tried the MojoSetup for Duke Nukem 3D? Download it [here](http://icculus.org/mojosetup/examples/duke3d/duke3d-mojosetup-linux-x86.bin). First, change the permissions on the installer:

```

chmod +x duke3d-mojosetup-linux-x86.bin

```

Then, to execute the installer (this will install it to your home directory):

```

./duke3d-mojosetup-linux-x86.bin

```

To run the game:
```

cd ~/duke3d; sh duke3d-bin

```

You will need the original CD to install the full version, but the installer will download and set up the shareware version for you if you don't own it. The MojoSetup for Duk3D is still alpha software, so it may or may not work for you.

---

### Post by fululian on 2007-10-24
thanks i'll try this one out. which version of the duke-ports does this installer install?

and another thing - does anyone know where the up and running jfduke32 saves the screenshots? if i punch F12, it saves the screen, but i do not know where to (or what the file is named anyway). ? thanks

---

