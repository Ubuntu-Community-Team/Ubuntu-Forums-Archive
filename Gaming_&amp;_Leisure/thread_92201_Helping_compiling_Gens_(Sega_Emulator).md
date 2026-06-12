---
title: "Helping compiling Gens (Sega Emulator)"
date: 2005-11-19
forum: Gaming &amp; Leisure
---

### Post by sirdeets on 2005-11-19
Hello all, I'm trying to build Gens from source, using the instructions from another thread here: [http://ubuntuforums.org/archive/index.php/t-28695.html](http://ubuntuforums.org/archive/index.php/t-28695.html)

Specifically, I grabbed the src from CVS using the instructions given in that thread,   by typing the following:
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gens login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gens co -P GensForLinux
```

I ran the configure script just fine... however, when I type "make", I eventually get the following:

```
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/anjuta_widget -I./gtkui/glade -I.   -DDATADIR=\"/usr/local/share/gens\" -I/usr/include/SDL -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -g -O2 -c -o emulator/gens-g_main.o `test -f emulator/g_main.c || echo './'`emulator/g_main.c
emulator/g_main.c: In function 'Init':
emulator/g_main.c:557: warning: incompatible implicit declaration of built-in function 'strncpy'
emulator/g_main.c:558: warning: incompatible implicit declaration of built-in function 'strcat'
emulator/g_main.c:567: warning: incompatible implicit declaration of built-in function 'strcpy'
emulator/g_main.c: In function 'main':
emulator/g_main.c:743: warning: incompatible implicit declaration of built-in function 'strncpy'
emulator/g_main.c:744: warning: incompatible implicit declaration of built-in function 'strcat'
emulator/g_main.c: At top level:
emulator/g_main.c:755: error: static declaration of 'Build_Language_String' follows non-static declaration
emulator/g_main.c:570: error: previous implicit declaration of 'Build_Language_String' was here
emulator/g_main.c: In function 'Build_Language_String':
emulator/g_main.c:845: warning: incompatible implicit declaration of built-in function 'strcpy'
make[3]: *** [emulator/gens-g_main.o] Error 1
```

Can anyone help me track down what's going wrong? I'd appreciate any help. Thanks!

---

### Post by sirdeets on 2005-11-24
bump... any help would be really appreciated :-\

---

### Post by chronusdark on 2005-12-22
same error perhaps its a bug?

---

### Post by chronusdark on 2005-12-22
got it

you have to do 

```
export CC=/usr/bin/gcc-3.4
./configure
make
make install
```

---

### Post by htinn on 2005-12-24
[QUOTE=chronusdark]got it

you have to do 

```
export CC=/usr/bin/gcc-3.4
./configure
make
make install
```[/QUOTE]

Thanks, that seems to work now (though it seems to lack gamepad support).

---

### Post by sirdeets on 2005-12-27
Wow, that was huge. Thanks a lot :smile: 

Out of curiosity, how did you know that this was the fix? 

As an aside, I can get the emulator to run fine, and can load games to boot. However, the games have no sound. Console output shows:
SDL: Audio timeout - buggy audio driver? (disabled)
audio: Bad file descriptor

Any ideas? Thanks again for the help!

---

### Post by linuxfanatic1024 on 2005-12-30
Thanks... I wrote some directions in the linked thread, but they stopped working after I upgraded to Breezy. I guess GCC 4.0 has problems with some software... Thanks for the tip on how to select a GCC version. I never really knew how to do that.

---

