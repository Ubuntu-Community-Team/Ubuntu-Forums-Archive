---
title: "Compiling Quake 3 under 64bit Ubuntu"
date: 2009-05-25
forum: Gaming &amp; Leisure
---

### Post by crazyfuturamanoob on 2009-05-25
I downloaded Quake 3 source code, unpacked the zip using "unzip -a". Then I tried to compile it, but it isn't amd64 compatible:
```

**/home/arho/quake3-1.32b/code$ ./unix/cons -- gcc=gcc g++=g++**

...

debug-x86-Linux-2.9/Q3/game/game/g_main.c: In function 'vmMain':
debug-x86-Linux-2.9/Q3/game/game/g_main.c:212: error: cast from pointer to integer of different size
debug-x86-Linux-2.9/Q3/game/game/g_main.c: In function 'FindIntermissionPoint':
debug-x86-Linux-2.9/Q3/game/game/g_main.c:942: error: cast from pointer to integer of different size
cons: *** [debug-x86-Linux-2.9/Q3/game/game/g_main.o] Error 1
cons: errors constructing debug-x86-Linux-2.9/Q3/game/game/g_main.o

```

I tried google but didn't find anything.

---

### Post by ruzkie on 2009-05-25
tried ioquake3?

---

### Post by LinuxFox on 2009-05-25
> **ruzkie said:**
> tried ioquake3?I also recommend ioquake3 if you just want to play Quake 3.  I don't know about compiling Quake 3's engine from source and I don't have a 64-bit computer, but I notice a 64-bit version available on the [ioquake3 website]("http://ioquake3.org/get-it/").

Only problem I noticed was "clipping graphics".  After I removed the extra "/" in the shortcut, it ran with no problems.

---

### Post by crazyfuturamanoob on 2009-05-26
I don't want to only play it but also learn modding, thats why I need the source. ioquake works great!

---

### Post by cartman_ on 2009-05-28
I guess it has to do with different size of types on 64b systems (not sure). But I managed to remove the first error by changing the line 212 to:
```
 return (int) (long) ClientConnect( arg0, arg1, arg2 );
```I don't think it's possible without code changes to compile a 64b version of it.

Also tried the -m32 switch for the gcc but I've got errors like this:

```
/usr/bin/ld: i386 architecture of input file `debug-x86-Linux-2.9/Q3/cgame/cgame/cg_main.o' is incompatible with i386:x86-64 output 
```I guess somewhere it does not use the gcc="gcc -m32" parameter and some of the output is in 32b and some in 64b.

Hope it helps.

Maybe [this]("http://www.viva64.com/content/articles/64-bit-development/?f=Application_port_to_64-bit_platforms_or_never_cackle_till_your_egg_is_laid.html&lang=en&content=64-bit-development") will also help?

---

