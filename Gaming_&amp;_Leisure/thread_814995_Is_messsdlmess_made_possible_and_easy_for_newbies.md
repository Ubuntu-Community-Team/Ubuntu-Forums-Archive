---
title: "Is mess/sdlmess made possible and easy for newbies ??"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-06-01
Hello,

Just thinking that mess is like his name : 
" a bunch of mess " and I absolutely not well programed for users.
 
They code, they are going fast, ok, but no one profit of it.

At least they enjoy their coding ;)

---

### Post by frenchn00b on 2008-06-01
I finally managed after spending hours !!! 
 
 
here is how I made it : 
Here is my script to install sdlmess !!
Finally 
to be retrieved [here]("http://yellowprotoss.ye.funpic.org/games/sdlmame/sdlmame0122-installer-ubuntu.sh") 
you can run it from the console directly.

```
#!/bin/bash
mkdir -p /usr/share/games/
cd /usr/share/games/
wget -N http://ftp.plusline.de/FreeBSD/distfiles/sdlmess0122.zip
unzip sdlmess0122.zip
rm sdlmess0122.zip
mv sdlmess0122 sdlmess
cd /usr/share/games/sdlmess
make -f makefile.sd
beep
chmod ug+rx /usr/share/games/sdlmess -R
mkdir -p /usr/share/games/sdlmess/roms
echo "please put all the zip files into /usr/share/games/sdlmess/roms, like this"
rox & rox &
echo "I am waiting you do so with rox and please press enter"
read lfkdjdlfs
rm /usr/bin/sdlmess 
ln -s /usr/share/games/sdlmess/mess   /usr/bin/sdlmess 
chmod ug+rx /usr/share/games/sdlmess -R
chmod ug+rx /usr/bin/sdlmess
echo "to run a floppy game : mess cpc464 -flop1 renegade.dsk"
echo "to run a console game : mess n64 -cart mario64.n64"
echo "Enjoy !!"

```

---

### Post by MonkeeSage on 2008-06-01
> **frenchn00b said:**
> I finally managed after spending hours !!! 
 
 
here is how I made it : 
Here is my script to install sdlmess !!
Finally 
to be retrieved [here]("http://yellowprotoss.ye.funpic.org/games/sdlmame/sdlmame0122-installer-ubuntu.sh") 
you can run it from the console directly.

```
#!/bin/bash
mkdir -p /usr/share/games/
cd /usr/share/games/
wget -N http://ftp.plusline.de/FreeBSD/distfiles/sdlmess0122.zip
unzip sdlmess0122.zip
rm sdlmess0122.zip
mv sdlmess0122 sdlmess
cd /usr/share/games/sdlmess
make -f makefile.sd
beep
chmod ug+rx /usr/share/games/sdlmess -R
mkdir -p /usr/share/games/sdlmess/roms
echo "please put all the zip files into /usr/share/games/sdlmess/roms, like this"
rox & rox &
echo "I am waiting you do so with rox and please press enter"
read lfkdjdlfs
rm /usr/bin/sdlmess 
ln -s /usr/share/games/sdlmess/mess   /usr/bin/sdlmess 
chmod ug+rx /usr/share/games/sdlmess -R
chmod ug+rx /usr/bin/sdlmess
echo "to run a floppy game : mess cpc464 -flop1 renegade.dsk"
echo "to run a console game : mess n64 -cart mario64.n64"
echo "Enjoy !!"

```

Hi,

Try this:

```

mkdir -p /usr/share/games/sdlmess/roms
cd /usr/share/games/
wget -c -N -U "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0" --referer="http://rbelmont.mameworld.info/?page_id=163" http://rbelmont.mameworld.info/sdlmess0125.zip
unzip sdlmess0125.zip
cd sdlmess0125
make -f makefile.sdl
beep
echo "please put all the zip files into /usr/share/games/sdlmess0125/roms"
ln -sf $PWD/mess /usr/bin/sdlmess 
echo "to run a floppy game : sdlmess cpc464 -flop1 renegade.dsk"
echo "to run a console game : sdlmess n64 -cart mario64.n64"

```

---

### Post by frenchn00b on 2008-06-01
thank you !!

I am still looking how to exit sdlmess, like a500n
the emulation of the amiga looks ok, even though I have no sound for the moment

If one does sdlmess -l, we cannot see all the possible machines.
sdlmess menu can only display few machines, in that menu, not all :(

---

### Post by frenchn00b on 2008-06-01
nope not working

```
make -f makefile.sdl
``` gives this error:

```
r -p obj/sdl/mess/mess/tools/imgtool/modules
mkdir -p obj/sdl/mess/mess/tools/messtest
mkdir -p obj/sdl/mess/mess/video
mkdir -p obj/sdl/mess/osd/sdl
mkdir -p obj/sdl/mess/tools
Compiling src/emu/cpu/m68000/m68kmake.c...
Compiling src/osd/sdl/strconv.c...
Compiling src/osd/sdl/sdldir.c...
Compiling src/osd/sdl/sdlfile.c...
Compiling src/osd/sdl/sdlmisc.c...
Compiling src/osd/sdl/sdlsync.c...
cc1: warnings being treated as errors
src/osd/sdl/sdlsync.c: In function ‘osd_thread_cpu_affinity’:
src/osd/sdl/sdlsync.c:594: warning: implicit declaration of function ‘pthread_setaffinity_np’
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
```

---

### Post by MonkeeSage on 2008-06-01
> **frenchn00b said:**
> nope not working

```
make -f makefile.sdl
``` gives this error:

```
r -p obj/sdl/mess/mess/tools/imgtool/modules
mkdir -p obj/sdl/mess/mess/tools/messtest
mkdir -p obj/sdl/mess/mess/video
mkdir -p obj/sdl/mess/osd/sdl
mkdir -p obj/sdl/mess/tools
Compiling src/emu/cpu/m68000/m68kmake.c...
Compiling src/osd/sdl/strconv.c...
Compiling src/osd/sdl/sdldir.c...
Compiling src/osd/sdl/sdlfile.c...
Compiling src/osd/sdl/sdlmisc.c...
Compiling src/osd/sdl/sdlsync.c...
cc1: warnings being treated as errors
src/osd/sdl/sdlsync.c: In function ‘osd_thread_cpu_affinity’:
src/osd/sdl/sdlsync.c:594: warning: implicit declaration of function ‘pthread_setaffinity_np’
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
```

Try installing libpthread-stubs0 / libpthread-stubs0-dev. I don't use mess so I'm not sure of any errors with it. Sorry.

---

### Post by MonkeeSage on 2008-06-05
Did you try installing those packages and recompiling?

---

