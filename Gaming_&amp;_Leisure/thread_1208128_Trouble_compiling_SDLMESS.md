---
title: "Trouble compiling SDLMESS"
date: 2009-07-08
forum: Gaming &amp; Leisure
---

### Post by kristy80 on 2009-07-08
Hopefully this is the right board to ask this, I saw other threads to this effect in here so I thought it must be.  I have been trying to compile sdlmess due to the fact that there is no known ubuntu packages for it. (Which doesn't make too much sense to me since there are packages for sdlmame) And have not been having much luck.  After all the makedir stuff I get this:

```
Compiling src/emu/cpu/m68000/m68kmake.c...
/bin/sh: sdl-config: not found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Compiling src/osd/sdl/strconv.c...
/bin/sh: sdl-config: not found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Compiling src/osd/sdl/sdldir.c...
/bin/sh: sdl-config: not found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Compiling src/osd/sdl/sdlfile.c...
/bin/sh: sdl-config: not found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Compiling src/osd/sdl/sdlmisc.c...
/bin/sh: sdl-config: not found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Compiling src/osd/sdl/sdlsync.c...
/bin/sh: sdl-config: not found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
src/osd/sdl/sdlsync.c:17:21: error: SDL/SDL.h: No such file or directory
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
```

I made sure that I had everything installed that SDLMESS needed so I don't know what could be going on since obviously other people have not had a problem with this. :confused:

---

### Post by BoyOfDestiny on 2009-07-08
Try
```
sudo apt-get install build-essential libsdl1.2-dev libgconf2-dev
sudo apt-get build-dep sdlmame
```

You may have the run time files needed, but you need the -dev files. sdlmame should use some of the same dependencies, if not all...

It's been too long since I installed what's needed to build sdlmess (once it's done, you pretty much just compile it from then on with no worries...) but for example that gconf error, you need libgconf2-dev

So any error, search synaptic or use apt-cache search if you prefer cli. Search for it with -dev on the end for sure, and sometimes pre-fixed with lib.

Depending on what systems you want emulated I recommend a look at mednafen. It's in the Ubuntu repos of course.
[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

---

### Post by Grishka on 2009-07-08
it looks like MAME is much more popular than MESS. that's a pity, MESS is an excellent, powerful piece of software. anyway, 32-bit packages are available from [Ludomatic](http://apt.ludomatic.fr/pool/non-free/s/sdlmess/), and he had 64-bit packages as well, don't know why he dropped them. if you still need to compile, you'll have to install libexpat1-dev, libsdl1.2-dev, zlib1g-dev, libxinerama-dev, libgconf2-dev and libgtk2.0-dev.

---

### Post by kristy80 on 2009-07-08
thank you for the tips, and I already have mednafen actually.  I just liked the idea of having all those systems under one program, and I wanted to see how far mess in general has progressed since I used it years ago.  I am really no stranger to compiling (I used to run slackware) but it has been a while and I didn't think about the fact that sometimes the dependacy lists don't consider the -devs seperate packages.

---

