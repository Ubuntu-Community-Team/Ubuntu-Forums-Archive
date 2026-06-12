---
title: "Neverball &quot;make&quot; help"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by phoenix5002 on 2008-03-15
I downloaded neverball and I got to the directory where the makefile is and type "sudo make" and I get a bunch of errors:

```
make: sdl-config: Command not found
cc -Wall -O3 -ansi  -Ishare -o share/image.o -c share/image.c
share/image.c:15:17: error: SDL.h: No such file or directory
share/image.c:16:21: error: SDL_ttf.h: No such file or directory
share/image.c:17:23: error: SDL_image.h: No such file or directory
In file included from share/image.c:22:
share/image.h:14: error: expected ‘)’ before ‘*’ token
share/image.h:15: error: expected ‘)’ before ‘*’ token
share/image.h:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
share/image.h:18: error: expected declaration specifiers or ‘...’ before ‘SDL_Surface’
share/image.h:22: error: expected declaration specifiers or ‘...’ before ‘TTF_Font’
share/image.c: In function ‘image_snap’:
share/image.c:33: error: ‘SDL_Surface’ undeclared (first use in this function)
share/image.c:33: error: (Each undeclared identifier is reported only once
share/image.c:33: error: for each function it appears in.)
share/image.c:33: error: ‘buf’ undeclared (first use in this function)
share/image.c:33: warning: implicit declaration of function ‘SDL_CreateRGBSurface’
share/image.c:33: error: ‘SDL_SWSURFACE’ undeclared (first use in this function)
share/image.c:35: error: ‘img’ undeclared (first use in this function)
share/image.c:44: warning: implicit declaration of function ‘SDL_SaveBMP’
share/image.c:46: warning: implicit declaration of function ‘SDL_FreeSurface’
share/image.c: At top level:
share/image.c:61: error: expected ‘)’ before ‘*’ token
share/image.c:87: error: expected ‘)’ before ‘*’ token
share/image.c:112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
share/image.c:166: error: expected declaration specifiers or ‘...’ before ‘SDL_Surface’
share/image.c: In function ‘make_image_from_surf’:
share/image.c:176: error: ‘SDL_Surface’ undeclared (first use in this function)
share/image.c:176: error: ‘d’ undeclared (first use in this function)
share/image.c:176: warning: implicit declaration of function ‘image_scale’
share/image.c:176: error: ‘s’ undeclared (first use in this function)
share/image.c: In function ‘make_image_from_file’:
share/image.c:222: error: ‘SDL_Surface’ undeclared (first use in this function)
share/image.c:222: error: ‘src’ undeclared (first use in this function)
share/image.c:223: error: ‘dst’ undeclared (first use in this function)
share/image.c:224: error: ‘SDL_Rect’ undeclared (first use in this function)
share/image.c:224: error: expected ‘;’ before ‘rect’
share/image.c:230: warning: implicit declaration of function ‘IMG_Load’
share/image.c:242: error: ‘SDL_SWSURFACE’ undeclared (first use in this function)
share/image.c:247: error: ‘rect’ undeclared (first use in this function)
share/image.c:247: error: ‘Sint16’ undeclared (first use in this function)
share/image.c:250: warning: implicit declaration of function ‘SDL_SetAlpha’
share/image.c:251: warning: implicit declaration of function ‘SDL_BlitSurface’
share/image.c:253: error: too many arguments to function ‘make_image_from_surf’
share/image.c: At top level:
share/image.c:270: error: expected declaration specifiers or ‘...’ before ‘TTF_Font’
share/image.c: In function ‘make_image_from_font’:
share/image.c:272: error: ‘SDL_Color’ undeclared (first use in this function)
share/image.c:272: error: expected ‘;’ before ‘fg’
share/image.c:274: error: ‘SDL_Surface’ undeclared (first use in this function)
share/image.c:274: error: ‘src’ undeclared (first use in this function)
share/image.c:275: error: ‘dst’ undeclared (first use in this function)
share/image.c:276: error: ‘SDL_Rect’ undeclared (first use in this function)
share/image.c:276: error: expected ‘;’ before ‘rect’
share/image.c:284: warning: implicit declaration of function ‘TTF_RenderText_Blended’
share/image.c:284: error: ‘font’ undeclared (first use in this function)
share/image.c:284: error: ‘fg’ undeclared (first use in this function)
share/image.c:296: error: ‘SDL_SWSURFACE’ undeclared (first use in this function)
share/image.c:301: error: ‘rect’ undeclared (first use in this function)
share/image.c:301: error: ‘Sint16’ undeclared (first use in this function)
share/image.c:307: warning: implicit declaration of function ‘image_white’
share/image.c:309: error: too many arguments to function ‘make_image_from_surf’
make: *** [share/image.o] Error 1

```

---

### Post by FrozenFox on 2008-03-15
It probably needs one of the libsdl or libsdl-dev files installed.. (aptitude search libdsl)

but in any case.. why are you compiling it?? It's in the repositories, you know.. at least, it is on hardy. I'm 90% sure there's a deb for it on gutsy too, as I used to have it..

---

### Post by Vadi on 2008-03-15
There's a much easier way to get it. Go to Applications - Add/Remove. For "show" on top-left, select "All avialable applications", and then type "neverball" in the filter.

Enable checkbox beside it, click on "Apply Changes", and it'll download & install it for you. You can then find it in Applications - Games.

Enjoy!

---

