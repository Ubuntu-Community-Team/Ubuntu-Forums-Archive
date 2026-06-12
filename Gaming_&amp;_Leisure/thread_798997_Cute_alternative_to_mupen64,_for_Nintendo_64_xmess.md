---
title: "Cute alternative to mupen64, for Nintendo 64: xmess.SDL"
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-05-18
Hello guys,

Some of you are already using the xmess program instead of mupen64?
  The drivers are located here: [http://mess.toseciso.org/mess:drivers:n64:n64](http://mess.toseciso.org/mess:drivers:n64:n64)
 
here is the code source to compile it: [http://mess.toseciso.org/_media/downloads:sdlmess0124.zip?id=downloads&cache=cache](http://mess.toseciso.org/_media/downloads:sdlmess0124.zip?id=downloads&cache=cache)

Are thou already xmess-N64 happy users, if there is some already ? :)

---

### Post by frenchn00b on 2008-05-18
```
/mess/tools/messtest
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
src/osd/sdl/sdlsync.c: In function &#8216;osd_thread_cpu_affinity&#8217;:
src/osd/sdl/sdlsync.c:594: warning: implicit declaration of function &#8216;pthread_setaffinity_np&#8217;
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1
```



of course devlpmnt sdl is installed 

> uYou need the SDL development package installed. If you get something like this, search for the base part of the filename missing (SDL in this case) plus dev and install the most likely candidate. Your case, you need the package libsdl1.2-dev installed.

  
I brutally added this, but still error here:

> apt-get install libsdl-net1.2 libsdl-image1.2-dev libsdl1.2debian-alsa  libsdl1.2debian  libsdl1.2-dev libsdl-stretch-dev  libsdl-console-dev   libsdl-gfx1.2-dev   libsdl-sound1.2-dev   libsdl-stretch-dev   libsdl-ttf2.0-dev  libsdl-sge-dev  libsdl-pango-dev  libsdl-gfx1.2-dev  libsdl-ocaml-dev  libsdl-sge-dev  libsdl-perl  libsdl-ruby1.8


> ded from src/osd/sdl/osinline.h:10,
                 from src/osd/sdl/sdlwork.c:20:
src/emu/eminline.h: In function &#8216;compare_exchange_ptr&#8217;:
src/emu/eminline.h:346: warning: cast from pointer to integer of different size
src/emu/eminline.h:346: warning: cast from pointer to integer of different size
src/emu/eminline.h:351: warning: cast to pointer from integer of different size
make: *** [obj/sdl/mess/osd/sdl/sdlwork.o] Error 1
make: *** Waiting for unfinished jobs....
cc1: warnings being treated as errors
In file included from src/osd/sdl/osinline.h:10,
                 from src/osd/sdl/sdlsync.c:29:
src/emu/eminline.h: In function &#8216;compare_exchange_ptr&#8217;:
src/emu/eminline.h:346: warning: cast from pointer to integer of different size
src/emu/eminline.h:346: warning: cast from pointer to integer of different size
src/emu/eminline.h:351: warning: cast to pointer from integer of different size
src/osd/sdl/sdlsync.c: In function &#8216;osd_thread_cpu_affinity&#8217;:
src/osd/sdl/sdlsync.c:594: warning: implicit declaration of function &#8216;pthread_setaffinity_np&#8217;
make: *** [obj/sdl/mess/osd/sdl/sdlsync.o] Error 1


---

### Post by DoktorSeven on 2008-05-18
You're getting warnings flagged as error messages which is not normal; there's nothing wrong with what you have installed.  This is a problem with the package you're trying to compile.

The latest SDLmess can be downloaded [here](http://rbelmont.mameworld.info/?page_id=163) and should compile fine, though I've never used SDLmess (or any version of MESS) so I'm not sure what to do about N64 compatibility.

---

