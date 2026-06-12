---
title: "MAME compilation issues"
date: 2011-05-01
forum: Gaming &amp; Leisure
---

### Post by ukyo_rulz on 2011-05-01
In the past, I've always downloaded and compiled my own MAME. Once version 0.141 came along, though, I started to run into errors. I figured that I could afford to skip a version, so I waited for 0.142 to come out. When I tried to compile 0.142, though, I got the same error. I don't really know how to fix it, and any help would be appreciated.

The error I get from "make -j3" is as follows:

------------------------------------------------
Compiling src/mame/machine/ticket.c...
Compiling src/mame/video/avgdvg.c...
Compiling src/osd/sdl/sdlmain.c...
Compiling src/osd/sdl/input.c...
src/osd/sdl/sdlmain.c:18:25: error: SDL/SDL_ttf.h: No such file or directory
src/osd/sdl/sdlmain.c:1013:72: error: "TTF_MAJOR_VERSION" is not defined
src/osd/sdl/sdlmain.c:1013:72: error: "TTF_MINOR_VERSION" is not defined
src/osd/sdl/sdlmain.c:1013:72: error: "TTF_PATCHLEVEL" is not defined
src/osd/sdl/sdlmain.c: In function ‘int main(int, char**)’:
src/osd/sdl/sdlmain.c:317: error: ‘TTF_Init’ was not declared in this scope
src/osd/sdl/sdlmain.c:319: error: ‘TTF_GetError’ was not declared in this scope
src/osd/sdl/sdlmain.c:366: error: ‘TTF_Quit’ was not declared in this scope
src/osd/sdl/sdlmain.c: At global scope:
src/osd/sdl/sdlmain.c:829: error: expected initializer before ‘*’ token
make: *** [obj/sdl/mame64/osd/sdl/sdlmain.o] Error 1
make: *** Waiting for unfinished jobs....
------------------------------------------------

I can still use my box to compile previous releases up till version 0.140 using "make -j3" but from 0.141 and up I get the above error.

---

### Post by Perfect Storm on 2011-05-01
> src/osd/sdl/sdlmain.c:18:25: error: SDL/SDL_ttf.h: No such file or directory

Install libsdl-ttf2.0-dev

---

### Post by ukyo_rulz on 2011-05-01
Worked like a charm. Thanks!

---

