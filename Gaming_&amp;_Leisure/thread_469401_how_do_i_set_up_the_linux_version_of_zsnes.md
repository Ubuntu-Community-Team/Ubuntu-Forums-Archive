---
title: "how do i set up the linux version of zsnes?"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by beanman25 on 2007-06-09
I have the zsnes151src.tar.bz2 file. what do I do now?

---

### Post by hikaricore on 2007-06-09
Well you will need to compile it (not sure what the dependancies are) after extracting the archive:

> tar -jxvf zsnes151src.tar.bz2

Usually the process of compiling is simple:

> 
cd zsnes151src
./configure
make
sudo make install

Or you can get the Ubuntu (feisty) package here: [http://www.getdeb.net/app.php?name=ZSNES](http://www.getdeb.net/app.php?name=ZSNES)

---

### Post by BoyOfDestiny on 2007-06-09
> **hikaricore said:**
> Well you will need to compile it (not sure what the dependancies are) after extracting the archive:



Usually the process of compiling is simple:



Or you can get the Ubuntu (feisty) package here: [http://www.getdeb.net/app.php?name=ZSNES](http://www.getdeb.net/app.php?name=ZSNES)

I think this should do it (installing the dependencies usually a one time step)

sudo apt-get install build-essential libsdl1.2-dev libpng12-dev nasm zlib1g-dev

For zsnes you'll want to do (after uncompressing as the poster showed above)
cd zsnesfolder
cd src

./autogen.sh
make

---

### Post by beanman25 on 2007-06-09
thanks for the help, I got it working.

---

### Post by beanman25 on 2007-06-09
wait, I used the deb installer but everytime i open it, there is a black screen. and it closes.

---

### Post by BoyOfDestiny on 2007-06-09
> **beanman25 said:**
> wait, I used the deb installer but everytime i open it, there is a black screen. and it closes.

That's not good. Try typing zsnes from terminal. See if any error messages pop up.

---

### Post by beanman25 on 2007-06-09
steve@steve-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
Illegal instruction (core dumped)
steve@steve-desktop:~$ 


cant i use the keyboard?

---

### Post by BoyOfDestiny on 2007-06-09
> **beanman25 said:**
> steve@steve-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
Illegal instruction (core dumped)
steve@steve-desktop:~$ 


cant i use the keyboard?

Strange, yeah you can use keyboard or gamepad (I switch between them pretty often...)

The core dump is bad Though.

If you want you can try the deb I built a while back on feisty.

[http://www.safaribans.com/ubuntu/dists/feisty/main/binary-i386/zsnes_1.51-1_i386.deb](http://www.safaribans.com/ubuntu/dists/feisty/main/binary-i386/zsnes_1.51-1_i386.deb)

---

### Post by beanman25 on 2007-06-09
steve@steve-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

This is a work in progress build. It contains code which
May or may not be complete

If this is supposed to be an official release, you forgot to
run configure with --enable-release, go rebuild.

Starting Mouse detection.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
Illegal instruction (core dumped)
steve@steve-desktop:~$ 


same thing, any ideas? I need tetris attack.

---

### Post by BoyOfDestiny on 2007-06-09
> **beanman25 said:**
> steve@steve-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

This is a work in progress build. It contains code which
May or may not be complete

If this is supposed to be an official release, you forgot to
run configure with --enable-release, go rebuild.

Starting Mouse detection.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
Illegal instruction (core dumped)
steve@steve-desktop:~$ 


same thing, any ideas? I need tetris attack.

I love tetris attack, although it never feels quite the same in an emulator (on a somewhat related note, romhacking.net has a translation patch for the japanese version, panel de pon, it didn't have mario series characters, they were added for us and europe release...) 

My only guess is missing dependencies... Did you try the 
sudo apt-get install stuff in my first post?

---

### Post by beanman25 on 2007-06-09
yep, went through everything. is panel de pon good?

---

### Post by BoyOfDestiny on 2007-06-09
> **beanman25 said:**
> yep, went through everything. is panel de pon good?

Same as tetris attack except for the character art and in game backgrounds. Even the up + L and a for hard mode is the same. 

So same problem? Do you want to try building it from source?

Also, did you have an old version of zsnes installed before? Maybe it's an old config file giving trouble?

---

### Post by beanman25 on 2007-06-09
i could try, is it tough?

---

### Post by BoyOfDestiny on 2007-06-09
> **beanman25 said:**
> i could try, is it tough?

After you do it once, should be a breeze.

Just extract the 1.51 tar.bz thing

cd into in the dir

then cd into the src dir

./autogen.sh

make

Look for errors along the way. Make sure you have autoconf and automake installed (you can grab them from synaptic)

I wonder if mesa-common-dev was missing, try this and then run it again. If not maybe building the source will be best.

sudo apt-get install build-essential nasm autoconf automake libsdl1.2-dev zlib1g-dev libpng12-dev mesa-common-dev libao-dev

Also, which ubuntu and what arch are you running. I'm not sure if zsnes will run on 64-bit without ia32 libs...

---

### Post by beanman25 on 2007-06-09
im going to bed, thanks for the help so far, I will let you know how its doing in the morning

---

### Post by BoyOfDestiny on 2007-06-09
> **beanman25 said:**
> im going to bed, thanks for the help so far, I will let you know how its doing in the morning

Ok, no problem. Hope we can get it working. Night.

---

### Post by beanman25 on 2007-06-10
when you say cd into the dir, how do I do that?

---

### Post by BoyOfDestiny on 2007-06-10
> **beanman25 said:**
> when you say cd into the dir, how do I do that?

from terminal

cd nameofdir

so something like
cd zsnes_151/src

---

### Post by dfreer on 2007-06-10
Instead of compiling you could try using a precompiled .deb...
If you do try compiling it again, post all of the output so that we can see what went wrong.

zsnes stores it's configuration files in ~/.zsnes by default, so if there is an old installation you could try deleting that.

And zsnes works on 64-bit, although getting libao to work is a bit of a pain.

---

### Post by beanman25 on 2007-06-10
steve@steve-desktop:~$ cd /home/steve/zsnes_1_51/src
steve@steve-desktop:~/zsnes_1_51/src$ ./autogen.sh
Generating build information using aclocal and autoconf...
./autogen.sh: 6: aclocal: not found
./autogen.sh: 7: autoconf: not found
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger
steve@steve-desktop:~/zsnes_1_51/src$

---

### Post by BoyOfDestiny on 2007-06-11
> **beanman25 said:**
> steve@steve-desktop:~$ cd /home/steve/zsnes_1_51/src
steve@steve-desktop:~/zsnes_1_51/src$ ./autogen.sh
Generating build information using aclocal and autoconf...
./autogen.sh: 6: aclocal: not found
./autogen.sh: 7: autoconf: not found
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger
steve@steve-desktop:~/zsnes_1_51/src$

fire up synaptic install libncurses5-dev and autoconf and automake

---

### Post by molex on 2007-06-11
There is no need to build ZSNES, it is available on the repository

Simply type in console

```
sudo apt-get install zsnes
```

---

### Post by hikaricore on 2007-06-11
> **molex said:**
> There is no need to build ZSNES, it is available on the repository

Simply type in console

```
sudo apt-get install zsnes
```

I don't believe it's the most recent version which was released after the feisty freeze.

Besides the OP needs to know how to compile eventually.

---

### Post by dfreer on 2007-06-11
> **hikaricore said:**
> I don't believe it's the most recent version which was released after the feisty freeze.

Besides the OP needs to know how to compile eventually.

Good point. Yeah, it's 1.42 If i remember correctly, and they fixed a lot of things in 1.51 as well as libao support. Compiliing isn't that hard and it is a good skill. 

Just install that ncurses library that was mentioned and then post the output again.

---

### Post by BigSilly on 2007-06-11
[GetDeb ]("http://www.getdeb.net/category.php?id=3")have the Debian package of version 1.51 available for download. Just download the file to your desktop (save it preferably) , double-click and the installer does the rest. I did it anyway and it's bang on.

Failing that (as if that isn't easy enough!) there isn't really a lot between 1.51 and the older version on Ubuntu's repositories. I've spoke to a few people who still use the older version because they reckon it performs better. I got the latest one myself from GetDeb and can't see a lot in it, but there it is. I would have been happy if I could only use v1.42. It's the one I used to use on XP for ages.

Let us know how you get on.

---

### Post by dfreer on 2007-06-11
> **BigSilly said:**
> 
Failing that (as if that isn't easy enough!) there isn't really a lot between 1.51 and the older version on Ubuntu's repositories. I've spoke to a few people who still use the older version because they reckon it performs better. I got the latest one myself from GetDeb and can't see a lot in it, but there it is. I would have been happy if I could only use v1.42. It's the one I used to use on XP for ages.

Let us know how you get on.

There's at least 0.09 difference!! ok, joking aside, there is a something major.
Libao support for linux. 
It improves sound quality greatly, plus there are a few movie making features (fluff) available. The windows version may not be much different, but that's windows :p

---

### Post by Megatog615 on 2007-06-12
Might be a good idea to use the current svn:

```
svn co https://svn.bountysource.com/zsnes/trunk zsnes
```

Enter the "zsnes" directory and do the normal build process.

---

### Post by halberd25 on 2007-06-22
I'm trying to compile this and I get this message:

ben@ben-laptop:~/Desktop/zsnes/src$ sh ./autogen.sh && gmake install Generating build information using aclocal and autoconf...
./autogen.sh: line 6: sdl-config: command not found
aclocal: couldn't open directory `/share/aclocal': No such file or directory
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
./configure: line 2951: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'./configure: line 2951: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
bash: gmake: command not found

I have lib5-ncurses as well as automake and autoconf installed.

I tried downloading the installer from getdeb and I see this message: Error: dependency not satisfiable: libc6

If anyone can help me resolve either method of installing this program, I'd really appreciate it.

---

### Post by dfreer on 2007-06-22
also install build-essential (if you haven't done so already), and libSDL -dev.
if you just want it installed try getting my zsnes, should be really easy to add the repository, and it will download anything you need to install it as well :)

---

### Post by halberd25 on 2007-06-22
I'm not sure if this helped.  I downloaded libsdl -dev, and it seemed to work.  When I tried to compile the package it said 'type 'make' and pray' so I typed make and got many lines of code (no error messges) and then nothing happened.  Is zsnes installed now?  If so, I can't find it.

Also, dfreer, I can't find your i386 package.

Here's the code I got after typing 'make'

ben@ben-laptop:~/Desktop/zsnes/src$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o tools/fileutil.o -c tools/fileutil.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o tools/strutil.o -c tools/strutil.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o tools/depbuild tools/depbuild.cpp tools/fileutil.o tools/strutil.o
tools/depbuild gcc " -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__   -I/usr/include/SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-fram e-pointer -s" nasm " -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O 1" cfg.o endmem.o init.o initc.o input.o md.o patch.o ui.o vcache.o version.o zl oader.o zmovie.o zpath.o zstate.o ztime.o ztimec.o chips/c4emu.o chips/c4proc.o chips/dsp1emu.o chips/dsp1proc.o chips/dsp2proc.o chips/dsp3emu.o chips/dsp3proc .o chips/dsp4emu.o chips/dsp4proc.o chips/fxemu2.o chips/fxemu2b.o chips/fxemu2c .o chips/fxtable.o chips/obc1emu.o chips/obc1proc.o chips/sa1proc.o chips/sa1reg s.o chips/sdd1emu.o chips/seta10.o chips/sfxproc.o chips/st10proc.o chips/7110pr oc.o chips/seta11.o chips/st11proc.o cpu/dma.o cpu/dsp.o cpu/dspproc.o cpu/execu te.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/memtable.o cpu/spc700.o cpu/stabl e.o cpu/table.o cpu/tablec.o debugasm.o debugger.o gui/gui.o gui/guifuncs.o gui/ menu.o effects/burn.o effects/smoke.o effects/water.o jma/7zlzma.o jma/crc32.o j ma/iiostrm.o    jma/inbyte.o jma/jma.o jma/lzma.o       jma/lzmadec.o jma/winout .o jma/zsnesjma.o mmlib/mm.o mmlib/linux.o  video/makev16b.o video/makev16t.o vi deo/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mode716e.o  video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/m716text. o video/newg162.o video/newgfx.o video/newgfx16.o video/newgfx2.o video/procvid. o video/procvidc.o video/sw_draw.o video/2xsaiw.o video/hq2x16.o video/hq2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o video/ntsc.o video/c opyvwin.o linux/audio.o linux/battery.o linux/sdlintrf.o linux/sdllink.o linux/g l_draw.o linux/sw_draw.o linux/safelib.o zip/unzip.o zip/zpng.o > makefile.dep
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o parsegen parsegen.cpp -lz
./parsegen  -D__UNIXSDL__ -D__OPENGL__ -gcc gcc -compile -flags " -pipe -I. -I/u sr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_REENTRANT -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -O1" -cheader cfg.h -f name cfg cfg.o cfg.psr
parsegen: gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/u sr/include/SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-poin ter -s -O1 -o cfg.o -c cfg.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o endmem.o e ndmem.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o init.o ini t.asm
./parsegen  -D__UNIXSDL__ -D__OPENGL__ -gcc gcc -compile -flags " -pipe -I. -I/u sr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_REENTRANT -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -O1" -cheader input.h -fname input input.o input.psr
parsegen: gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/u sr/include/SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-poin ter -s -O1 -o input.o -c input.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o initc.o -c initc.c
./parsegen  -D__UNIXSDL__ -D__OPENGL__ -gcc gcc -compile -flags " -pipe -I. -I/u sr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_REENTRANT -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -O1" -cheader md.h -fn ame md md.o md.psr
parsegen: gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/u sr/include/SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-poin ter -s -O1 -o md.o -c md.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o patch.o -c patch.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o ui.o -c ui.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o vcache.o v cache.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o version.o -c version.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o zloader.o -c zloader.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o zmovie.o -c zmovie.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o zpath.o -c zpath.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o zstate.o -c zstate.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o ztime.o zt ime.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o ztimec.o -c ztimec.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/c4emu.o -c chips/c4emu.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/c4pr oc.o chips/c4proc.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/dsp1emu.o -c chips/dsp1emu.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/dsp1 proc.o chips/dsp1proc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/dsp2 proc.o chips/dsp2proc.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/dsp3emu.o -c chips/dsp3emu.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/dsp3 proc.o chips/dsp3proc.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/dsp4emu.o -c chips/dsp4emu.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/dsp4 proc.o chips/dsp4proc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/fxem u2.o chips/fxemu2.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/fxem u2b.o chips/fxemu2b.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/fxem u2c.o chips/fxemu2c.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/fxta ble.o chips/fxtable.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/obc1emu.o -c chips/obc1emu.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/obc1 proc.o chips/obc1proc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/sa1p roc.o chips/sa1proc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/sa1r egs.o chips/sa1regs.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/sdd1emu.o -c chips/sdd1emu.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/seta10.o -c chips/seta10.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/sfxp roc.o chips/sfxproc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/st10 proc.o chips/st10proc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/7110 proc.o chips/7110proc.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o chips/seta11.o -c chips/seta11.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o chips/st11 proc.o chips/st11proc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/dma.o cpu/dma.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/dsp.o cpu/dsp.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/dsppro c.o cpu/dspproc.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/execut e.o cpu/execute.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o cpu/executec.o -c cpu/executec.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/irq.o cpu/irq.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/memory .o cpu/memory.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o cpu/memtable.o -c cpu/memtable.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/spc700 .o cpu/spc700.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/stable .o cpu/stable.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/table. o cpu/table.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o cpu/tablec .o cpu/tablec.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o debugasm.o  debugasm.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o debugger.o -c debugger.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o gui/gui.o gui/gui.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o gui/guifuncs.o -c gui/guifuncs.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o gui/menu.o  gui/menu.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o effects/burn.o -c effects/burn.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o effects/smoke.o -c effects/smoke.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o effects/water.o -c effects/water.c
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/7zlzma.o -c jma/7zlzma.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/crc32.o -c jma/crc32.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/iiostrm.o -c jma/iiostrm.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/inbyte.o -c jma/inbyte.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/jma.o -c jma/jma.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/lzma.o -c jma/lzma.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/lzmadec.o -c jma/lzmadec.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/winout.o -c jma/winout.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fn o-rtti -o jma/zsnesjma.o -c jma/zsnesjma.cpp
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o mmlib/mm.o -c mmlib/mm.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o mmlib/linux.o -c mmlib/linux.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/make v16b.o video/makev16b.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/make v16t.o video/makev16t.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/make vid.o video/makevid.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 716.o video/mode716.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 716b.o video/mode716b.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 716d.o video/mode716d.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 716e.o video/mode716e.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 716t.o video/mode716t.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 7.o video/mode7.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mode 7ext.o video/mode7ext.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/mv16 tms.o video/mv16tms.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/m716 text.o video/m716text.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/newg 162.o video/newg162.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/newg fx.o video/newgfx.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/newg fx16.o video/newgfx16.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/newg fx2.o video/newgfx2.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/proc vid.o video/procvid.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o video/procvidc.o -c video/procvidc.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/sw_d raw.o video/sw_draw.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/2xsa iw.o video/2xsaiw.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/hq2x 16.o video/hq2x16.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/hq2x 32.o video/hq2x32.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/hq3x 16.o video/hq3x16.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/hq3x 32.o video/hq3x32.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/hq4x 16.o video/hq4x16.asm
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/hq4x 32.o video/hq4x32.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o video/ntsc.o -c video/ntsc.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o video/copy vwin.o video/copyvwin.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o linux/audio.o -c linux/audio.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o linux/battery.o -c linux/battery.c
nasm  -w-orphan-labels -D__UNIXSDL__ -f elf -DELF -D__OPENGL__ -O1 -o linux/sdli ntrf.o linux/sdlintrf.asm
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o linux/sdllink.o -c linux/sdllink.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o linux/gl_draw.o -c linux/gl_draw.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o linux/sw_draw.o -c linux/sw_draw.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o linux/safelib.o -c linux/safelib.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o zip/unzip.o -c zip/unzip.c
gcc  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include /SDL -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -o zip/zpng.o -c zip/zpng.c
g++ -o zsnes cfg.o endmem.o init.o initc.o input.o md.o patch.o ui.o vcache.o ve rsion.o zloader.o zmovie.o zpath.o zstate.o ztime.o ztimec.o chips/c4emu.o chips /c4proc.o chips/dsp1emu.o chips/dsp1proc.o chips/dsp2proc.o chips/dsp3emu.o chip s/dsp3proc.o chips/dsp4emu.o chips/dsp4proc.o chips/fxemu2.o chips/fxemu2b.o chi ps/fxemu2c.o chips/fxtable.o chips/obc1emu.o chips/obc1proc.o chips/sa1proc.o ch ips/sa1regs.o chips/sdd1emu.o chips/seta10.o chips/sfxproc.o chips/st10proc.o ch ips/7110proc.o chips/seta11.o chips/st11proc.o cpu/dma.o cpu/dsp.o cpu/dspproc.o  cpu/execute.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/memtable.o cpu/spc700.o  cpu/stable.o cpu/table.o cpu/tablec.o debugasm.o debugger.o gui/gui.o gui/guifu ncs.o gui/menu.o effects/burn.o effects/smoke.o effects/water.o jma/7zlzma.o jma /crc32.o jma/iiostrm.o  jma/inbyte.o jma/jma.o jma/lzma.o       jma/lzmadec.o jm a/winout.o jma/zsnesjma.o mmlib/mm.o mmlib/linux.o  video/makev16b.o video/makev 16t.o video/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mo de716e.o video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/m 716text.o video/newg162.o video/newgfx.o video/newgfx16.o video/newgfx2.o video/ procvid.o video/procvidc.o video/sw_draw.o video/2xsaiw.o video/hq2x16.o video/h q2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o video/ntsc.o  video/copyvwin.o linux/audio.o linux/battery.o linux/sdlintrf.o linux/sdllink.o  linux/gl_draw.o linux/sw_draw.o linux/safelib.o zip/unzip.o zip/zpng.o  -pipe - I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_REEN TRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fno-rtti  -L/u sr/local/lib -L/usr/lib  -lz -L/usr/lib -lSDL -lpthread  -lpng -lm -lcurses -L/u sr/X11R6/lib -lGL
rm -f version.o

---

### Post by dfreer on 2007-06-22
it looks like it got made fine. do a ls -l in that directory, you should be able to see a program called zsnes. type ./zsnes and if everything went well you should see it working!

if it works, to actually install it though, there's two things you can do:
sudo make install
OR
sudo checkinstall

make install will simply install it, so it should run by just typing zsnes. but in order to remove it you would have to keep track of the files it installed, and then manually remove them. checkinstall will create a *.deb package before it installs, and you can then uninstall the package with sudo dpkg -r zsnes (or whatever name you gave to the package in checkinstall).

as for the repository, did you do this?
```
echo "deb http://packages.dfreer.org feisty main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org/5A22BD68.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install zsnes
```

That should work just fine, if nothing else try this direct link, save it to your desktop, and then double-click it. [http://packages.dfreer.org/pool/feisty/main/binary-i386/Z/zsnes_1.510-1.2_i386.deb](http://packages.dfreer.org/pool/feisty/main/binary-i386/Z/zsnes_1.510-1.2_i386.deb)

---

### Post by halberd25 on 2007-06-22
I tried your package, and it installed, but the program wouldn't run after I clicked on the icon.

The 'make install' command seemed to work just fine, though, thanks.

---

### Post by dfreer on 2007-06-22
hmmm. I'll look into why the icon isn't working. Honestly, I need to sit down with some nice clean 32/64 bit installs and get these freaking packages working ASAP :P
glad make install worked for you. if you run into sound issues, you might want to look into compiling with libao support enabled.

---

### Post by halberd25 on 2007-06-23
Yeah, the sound is actually really bad.  How do I compile with libao support enabled?

---

### Post by BoyOfDestiny on 2007-06-23
> **halberd25 said:**
> Yeah, the sound is actually really bad.  How do I compile with libao support enabled?

./configure --enable-libao

You can do a ./configure --help to get a listing of the all the possible stuff...

Anyway, good news, gutsy gibbon (next ubuntu release) has zsnes 1.51, and sound is perfect (so I'm guessing it's built with libao support) Or maybe it's the new alsa or something, even neverball (which sounded a bit staticky for me, is now perfect! :) )

---

### Post by halberd25 on 2007-06-23
it says "error: couldn't find libao," but I have it installed.

---

### Post by po0f on 2007-06-23
halberd25,

Install [libao-dev](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libao-dev&searchon=names&subword=1&version=all&release=all) and you should be all set to compile with libao support.  :)

---

### Post by halberd25 on 2007-06-23
Now when I run make, nothing shows up in /usr/local/bin.

edit: oh and dfreer, when trying to run zsnes from your package, it says something about needing glibc_2.4

---

### Post by po0f on 2007-06-23
halberd25,

Did you run `make install` afterwards?  And which version of Ubuntu or derivative are you using?

---

### Post by halberd25 on 2007-06-23
ok, make install seemed to fix it, but the sound quality is even worse than before.  I noticed this time when I enabled libao on configure, it gave me this

SDL support                   Version 1.2.9
NASM support                  NASM version 0.98.38 compiled on Jun 27 2005
zlib support                  Version 1.2.3
PNG support                   Yes, version 1.2.8
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

Whereas it used to say zsnes debugger disabled and also had a line that said libao enabled.

I'm running 6.06, btw.

---

### Post by po0f on 2007-06-23
halberd25,

Which options did you explicitly pass to the configure script?  Try enabling the `--enable-release` flag.

And if your only gripe is sound quality, just install [libsdl1.2debian-oss](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsdl1.2debian-oss&searchon=names&subword=1&version=all&release=all).  It fixed the problem for me.  :)

---

### Post by halberd25 on 2007-06-23
I tried switching to libsdl1.2debian-oss and I didn't notice a difference.  Also, --enable-release did nothing for me.  I don't know if this is of any relevence, but when I unchecked the "enable sound" box in zsnes, the sound continued to play.

---

### Post by dfreer on 2007-06-23
you should also run zsnes with -ad oss, if you compile with libao support.
```
./zsnes -ad oss
```

EDIT: did you try installing the glibc library it complained about? I haven't tested my packages on 6.06, which may explain your problems with my repository. I'll see if I can fix this for ya

---

### Post by halberd25 on 2007-06-23
I'm getting a whole bunch of error messages now for your zsnes, dfreer.

I compiled 1.51 with release and now when I run zsnes there's no sound.  In the terminal it says "Audio Open Failed"

edit: so I tried all of the sound options zsnes had, installing the appropriate package from synaptic manager for each one.  For all of them except for arts, the audio open failed (arts was unable to make some kind of folder or something and wouldn't run the program at all).  Finally I tried running it with esound installed using 'ad -sdl' and, lo and behold, perfect sound quality.

---

### Post by poobslag on 2007-12-03
thank you, this thread has been very helpful. i still can not get zsnes compiled. i am running an amd64 processor which may be complicating things. i have done the following:

sudo apt-get install automake
sudo apt-get install build-essential libsdl1.2-dev libpng12-dev nasm zlib1g-dev
sudo apt-get install libncurses5-dev
./autogen.sh
sudo apt-get install libao-dev
make

Currently, I'm stuck on make - the make command is still failing with a lot of these errors:

/usr/bin/ld: i386 architecture of input file `cpu/dma.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `cpu/dsp.o' is incompatible with i386:x86-64 output

There's about 3 dozen of these errors but they all look about the same. If anybody could throw me a bone that would be great, I'd like to run ZSNES - if there's an easier way than compiling, that's fine too. i tried apt-get zsnes but it said the package was unavailable (possibly because there's no version compiled for amd64 yet?)

---

### Post by dfreer on 2007-12-04
zsnes cannot be compiled as a 64-bit program, due to way it is made. Since AMD64 is capable of running 32-bit programs, the current solution is to compile zsnes as a 32-bit program, then install the 32-bit shared libraries it needs and run it in your 64-bit OS.

AFAIK, no one has been able to get zsnes to compile for a 32-bit target on a 64-bit Ubuntu machine. So what I'd recommend that you do is:
(1). Compile zsnes on a 32-bit machine, and then grab the binary and run it on your 64-bit machine.
(2). Grab the zsnes 32-bit package from the official repositories, extract the files to find the 32-bit binary and then run it on your 64-bit machine.
(3). Click on my link below and install my 64-bit package, which is basically the 32-bit binary wrapped in a 64-bit package so it will install correctly, plus it includes the needed 32-bit libraries to correctly run zsnes.

---

