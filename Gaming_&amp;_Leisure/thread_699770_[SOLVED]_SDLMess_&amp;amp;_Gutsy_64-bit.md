---
title: "[SOLVED] SDLMess &amp;amp; Gutsy 64-bit"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by EnigMattic on 2008-02-17
Hi
I'm having trouble getting [SDLMess (from here)]("http://rbelmont.mameworld.info/?page_id=163") to compile.

I have read in a couple of places that I should use the following command after extracting to :/usr/share/games/sdlmess and cd-ing to that directory:
```

make -f makefile.sdl PTR64=1 -j3
```

But I get these errors:
```
Compiling src/osd/sdl/sdltime.c...
src/osd/sdl/sdlsync.c:17:21: error: SDL/SDL.h: No such file or directory
Compiling src/osd/sdl/sdlwork.c...
src/osd/sdl/sdltime.c:13:21: error: SDL/SDL.h: No such file or directory
src/osd/sdl/sdltime.c: In function ‘init_cycle_counter’:
src/osd/sdl/sdltime.c:195: warning: implicit declaration of function ‘SDL_GetTicks’
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
make: *** Waiting for unfinished jobs....
make: *** [obj/sdl/mess/osd/sdl/sdltime.o] Error 1
```

Any Ideas? :confused:
All help greatly appreciated! :-)

---

### Post by homerhomer on 2008-02-17
yeah, I had some issue with that a while back

I resorted to mednafen

it' s in the repos and at

[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

---

### Post by DoktorSeven on 2008-02-17
> **EnigMattic said:**
> Hi
```
Compiling src/osd/sdl/sdltime.c...
src/osd/sdl/sdlsync.c:17:21: error: SDL/SDL.h: No such file or directory
```

You need the SDL *development* package installed.  If you get something like this, search for the base part of the filename missing (SDL in this case) plus **dev** and install the most likely candidate.  Your case, you need the package **libsdl1.2-dev** installed.

---

### Post by EnigMattic on 2008-02-18
> **DoktorSeven said:**
> You need the SDL *development* package installed.  If you get something like this, search for the base part of the filename missing (SDL in this case) plus **dev** and install the most likely candidate.  Your case, you need the package **libsdl1.2-dev** installed.

Thanks! That seems to have done it!

---

### Post by frenchn00b on 2008-05-18
I have this error messga. What could it be ?

*```
# make -f makefile.sdl TARGET=mess OSD=sdl TARGETOS=unix
Compiling src/osd/sdl/sdlsync.c...
cc1: warnings being treated as errors
src/osd/sdl/sdlsync.c: In function ‘osd_thread_cpu_affinity’:
src/osd/sdl/sdlsync.c:594: warning: implicit declaration of function ‘pthread_setaffinity_np’
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
laptop06:/tmp/s/sdlmess0125# make -f makefile.sdl
Compiling src/osd/sdl/sdlsync.c...
cc1: warnings being treated as errors
src/osd/sdl/sdlsync.c: In function ‘osd_thread_cpu_affinity’:
src/osd/sdl/sdlsync.c:594: warning: implicit declaration of function ‘pthread_setaffinity_np’
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
```

---

### Post by frenchn00b on 2008-05-18
no sdlmess can be found

[http://apt.ludomatic.fr/?hl=en#ekd](http://apt.ludomatic.fr/?hl=en#ekd) here, it has only debs for the sdlmame :(

---

### Post by frenchn00b on 2008-05-18
Even tried the fedora packages rpm with alien -i :

[http://dribble.org.uk/repo/8/i386/sdlmess-0124-1.fc8.drb.i386.rpm](http://dribble.org.uk/repo/8/i386/sdlmess-0124-1.fc8.drb.i386.rpm)

 no way to get sdlmess :(

---

