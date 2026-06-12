---
title: "foobillard-3.0a"
date: 2005-12-26
forum: Gaming &amp; Leisure
---

### Post by shaj on 2005-12-26
Hi all.

I'm havin problems installin foobillard on breezy. Not sure what I'm doin wrong or if I'm missin any files.

Are there any step by step guides or anythin on how to install the game?

Any help would be appreciated.

---

### Post by Perfect Storm on 2005-12-26
please decribe how you're trying to install it? From source, .deb other?
Any errors from the terminal?

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]please decribe how you're trying to install it? From source, .deb other?
Any errors from the terminal?[/QUOTE]

I extracted the source file (downloaded from the website). Didn't find any .deb files :(

Then I followed the instructions:

./configure
make
make install


the 'configure' bit woked fine...

then seem to be gettin some sorta error at make and make install


Making all in src
make[1]: Entering directory `/home/shaj/Gamez/foobillard-3.0a/src'
make  all-am
make[2]: Entering directory `/home/shaj/Gamez/foobillard-3.0a/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT billard3d.o -MD -MP -MF ".deps/billard3d.Tpo" \
  -c -o billard3d.o `test -f 'billard3d.c' || echo './'`billard3d.c; \
then mv ".deps/billard3d.Tpo" ".deps/billard3d.Po"; \
else rm -f ".deps/billard3d.Tpo"; exit 1; \
fi
/bin/sh: sdl-config: command not found
billard3d.c:32:20: error: GL/glu.h: No such file or directory
billard3d.c: In function ‘free_cuberef_tex’:
billard3d.c:4001: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
billard3d.c: In function ‘reassign_and_gen_cuberef_tex’:
billard3d.c:4024: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
billard3d.c: In function ‘Init’:
billard3d.c:4773: warning: implicit declaration of function ‘gluBuild2DMipmaps’
make[2]: *** [billard3d.o] Error 1
make[2]: Leaving directory `/home/shaj/Gamez/foobillard-3.0a/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/shaj/Gamez/foobillard-3.0a/src'
make: *** [all-recursive] Error 1

---

### Post by Perfect Storm on 2005-12-26
Try install another version of gcc

```

sudo apt-get install gcc-3.4 gcc-3.3-base

```

and try all over again.

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]Try install another version of gcc

```

sudo apt-get install gcc-3.4 gcc-3.3-base

```

and try all over again.[/QUOTE]

Okay...I've just looked at my Synaptic Package manager...

did a search on gcc

both gcc-3.4 & gcc-3.3-base have been installed already

tried it anyways and it gave me the 'already the latest' msg for both...

what next? :(

---

### Post by Perfect Storm on 2005-12-26
Hmmm......does it have a website I can take a closer look at?

As I see it it's missing something from sdl libs? did you installed the correct SDL's?

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]Hmmm......does it have a website I can take a closer look at?

As I see it it's missing something from sdl libs? did you installed the correct SDL's?[/QUOTE]

[http://foobillard.sunsite.dk/](http://foobillard.sunsite.dk/)

it's got a seperate configure command if u wanna use SDL. The default uses GLUT which is what I wanna use...

---

### Post by Perfect Storm on 2005-12-26
And you have **freeglut3-dev**, **libglut3-dev** **libglu1-mesa-dev** installed?

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]And you have **freeglut3-dev**, **libglut3-dev** **libglu1-mesa-dev** installed?[/QUOTE]

ok...didn't have those installed...

just installed em n ran make again...

much much more errors

n most of em seem to be SDL related...

I'm confused :(

---

### Post by Perfect Storm on 2005-12-26
please post

---

### Post by Perfect Storm on 2005-12-26
```
sudo apt-get install libsdl1.2debian libsdl1.2debian-all libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev libsdl-ttf1.2-dev
```

That should cover it. Remember to run ./configure again

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]```
sudo apt-get install libsdl1.2debian libsdl1.2debian-all libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev libsdl-ttf1.2-dev
```

That should cover it. Remember to run ./configure again[/QUOTE]

did all that...

deleted old foobillard & extracted a new copy of file

ran ./configure

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking ft2build.h usability... no
checking ft2build.h presence... no
checking for ft2build.h... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for socket... yes
checking for poll... yes
checking "for SDL support"... "yes"
checking "for glut support"... "no"
configure: creating ./config.status
config.status: creating Makefile
config.status: creating foobillard.spec
config.status: creating foobillard-SDL.spec
config.status: creating src/Makefile
config.status: creating data/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
```

ran make

```
Making all in src
make[1]: Entering directory `/home/shaj/Gamez/foobillard-3.0a/src'
make  all-am
make[2]: Entering directory `/home/shaj/Gamez/foobillard-3.0a/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT billard3d.o -MD -MP -MF ".deps/billard3d.Tpo" \
  -c -o billard3d.o `test -f 'billard3d.c' || echo './'`billard3d.c; \
then mv ".deps/billard3d.Tpo" ".deps/billard3d.Po"; \
else rm -f ".deps/billard3d.Tpo"; exit 1; \
fi
billard3d.c: In function ‘free_cuberef_tex’:
billard3d.c:4001: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
billard3d.c: In function ‘reassign_and_gen_cuberef_tex’:
billard3d.c:4024: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
billard3d.c: At top level:
billard3d.c:213: warning: ‘half_full_names’ defined but not used
billard3d.c: In function ‘create_cuberef_map’:
billard3d.c:2580: warning: ‘target’ may be used uninitialized in this function
billard3d.c: In function ‘DisplayFunc’:
billard3d.c:2919: warning: ‘eye_offs1’ may be used uninitialized in this function
billard3d.c:2906: warning: ‘eye_offs0’ may be used uninitialized in this function
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT billmove.o -MD -MP -MF ".deps/billmove.Tpo" \
  -c -o billmove.o `test -f 'billmove.c' || echo './'`billmove.c; \
then mv ".deps/billmove.Tpo" ".deps/billmove.Po"; \
else rm -f ".deps/billmove.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT billard.o -MD -MP -MF ".deps/billard.Tpo" \
  -c -o billard.o `test -f 'billard.c' || echo './'`billard.c; \
then mv ".deps/billard.Tpo" ".deps/billard.Po"; \
else rm -f ".deps/billard.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT vmath.o -MD -MP -MF ".deps/vmath.Tpo" \
  -c -o vmath.o `test -f 'vmath.c' || echo './'`vmath.c; \
then mv ".deps/vmath.Tpo" ".deps/vmath.Po"; \
else rm -f ".deps/vmath.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT ball.o -MD -MP -MF ".deps/ball.Tpo" \
  -c -o ball.o `test -f 'ball.c' || echo './'`ball.c; \
then mv ".deps/ball.Tpo" ".deps/ball.Po"; \
else rm -f ".deps/ball.Tpo"; exit 1; \
fi
ball.c:125: warning: pointer targets in initialization differ in signedness
ball.c:202: warning: pointer targets in initialization differ in signedness
ball.c: In function ‘ball_subdivide_nonrec’:
ball.c:499: warning: unused variable ‘rho’
ball.c: In function ‘draw_balls’:
ball.c:1581: warning: implicit declaration of function ‘glGenProgramsNV’
ball.c:1582: warning: implicit declaration of function ‘glBindProgramNV’
ball.c:1583: warning: implicit declaration of function ‘glLoadProgramNV’
ball.c:1583: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
ball.c:1796: warning: implicit declaration of function ‘glTrackMatrixNV’
ball.c:1800: warning: implicit declaration of function ‘glProgramParameter4fNV’
ball.c: At top level:
ball.c:58: warning: ‘fresnel_vert_prog_world_coord_str’ defined but not used
ball.c:215: warning: ‘col_null’ defined but not used
ball.c:264: warning: ‘in_array_old’ defined but not used
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT png_loader.o -MD -MP -MF ".deps/png_loader.Tpo" \
  -c -o png_loader.o `test -f 'png_loader.c' || echo './'`png_loader.c; \
then mv ".deps/png_loader.Tpo" ".deps/png_loader.Po"; \
else rm -f ".deps/png_loader.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT table.o -MD -MP -MF ".deps/table.Tpo" \
  -c -o table.o `test -f 'table.c' || echo './'`table.c; \
then mv ".deps/table.Tpo" ".deps/table.Po"; \
else rm -f ".deps/table.Tpo"; exit 1; \
fi
table.c: In function ‘create_table’:
table.c:1190: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
table.c:1192: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
table.c:1206: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
table.c:1208: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
table.c:1224: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
table.c:1226: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
table.c:1796: warning: unused variable ‘pass’
table.c:1156: warning: unused variable ‘s_gen_params’
table.c:1155: warning: unused variable ‘t_gen_params’
table.c:1128: warning: unused variable ‘cm’
table.c:1111: warning: unused variable ‘bumpcloth’
table.c:1108: warning: unused variable ‘bump_cloth_init’
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT queue.o -MD -MP -MF ".deps/queue.Tpo" \
  -c -o queue.o `test -f 'queue.c' || echo './'`queue.c; \
then mv ".deps/queue.Tpo" ".deps/queue.Po"; \
else rm -f ".deps/queue.Tpo"; exit 1; \
fi
queue.c: In function ‘delete_queue_texbind’:
queue.c:142: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
queue.c: In function ‘create_queue_texbind’:
queue.c:150: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
queue.c: In function ‘draw_queue’:
queue.c:194: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT aiplayer.o -MD -MP -MF ".deps/aiplayer.Tpo" \
  -c -o aiplayer.o `test -f 'aiplayer.c' || echo './'`aiplayer.c; \
then mv ".deps/aiplayer.Tpo" ".deps/aiplayer.Po"; \
else rm -f ".deps/aiplayer.Tpo"; exit 1; \
fi
aiplayer.c: In function ‘ai_get_stroke_dir_snooker’:
aiplayer.c:278: warning: ‘min_r_hit.z’ may be used uninitialized in this function
aiplayer.c:278: warning: ‘min_r_hit.y’ may be used uninitialized in this function
aiplayer.c:278: warning: ‘min_r_hit.x’ may be used uninitialized in this function
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT options.o -MD -MP -MF ".deps/options.Tpo" \
  -c -o options.o `test -f 'options.c' || echo './'`options.c; \
then mv ".deps/options.Tpo" ".deps/options.Po"; \
else rm -f ".deps/options.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT evaluate_move.o -MD -MP -MF ".deps/evaluate_move.Tpo" \
  -c -o evaluate_move.o `test -f 'evaluate_move.c' || echo './'`evaluate_move.c; \
then mv ".deps/evaluate_move.Tpo" ".deps/evaluate_move.Po"; \
else rm -f ".deps/evaluate_move.Tpo"; exit 1; \
fi
evaluate_move.c: In function ‘evaluate_last_move_snooker’:
evaluate_move.c:409: warning: enumeration value ‘SN_DONE’ not handled in switch
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT helpscreen.o -MD -MP -MF ".deps/helpscreen.Tpo" \
  -c -o helpscreen.o `test -f 'helpscreen.c' || echo './'`helpscreen.c; \
then mv ".deps/helpscreen.Tpo" ".deps/helpscreen.Po"; \
else rm -f ".deps/helpscreen.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT textobj.o -MD -MP -MF ".deps/textobj.Tpo" \
  -c -o textobj.o `test -f 'textobj.c' || echo './'`textobj.c; \
then mv ".deps/textobj.Tpo" ".deps/textobj.Po"; \
else rm -f ".deps/textobj.Tpo"; exit 1; \
fi
textobj.c: In function ‘create_string_quad’:
textobj.c:96: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
textobj.c:91: warning: unused variable ‘ny’
textobj.c:91: warning: unused variable ‘nx’
textobj.c:91: warning: unused variable ‘h2’
textobj.c:91: warning: unused variable ‘h1’
textobj.c:91: warning: unused variable ‘w2’
textobj.c:91: warning: unused variable ‘w1’
textobj.c: In function ‘textObj_toggle3D’:
textobj.c:204: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
textobj.c: In function ‘textObj_setText’:
textobj.c:227: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
textobj.c: In function ‘textObj_setHeight’:
textobj.c:271: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
textobj.c: In function ‘textObj_setFont’:
textobj.c:300: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
textobj.c: In function ‘textObj_delete’:
textobj.c:389: warning: pointer targets in passing argument 2 of ‘glDeleteTextures’ differ in signedness
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT font.o -MD -MP -MF ".deps/font.Tpo" \
  -c -o font.o `test -f 'font.c' || echo './'`font.c; \
then mv ".deps/font.Tpo" ".deps/font.Po"; \
else rm -f ".deps/font.Tpo"; exit 1; \
fi
font.c: In function ‘makeGLGeometryFT’:
font.c:374: warning: unused variable ‘v’
font.c:373: warning: unused variable ‘start_y’
font.c:373: warning: unused variable ‘start_x’
font.c:372: warning: unused variable ‘tobj’
font.c:370: warning: unused variable ‘j’
font.c:370: warning: unused variable ‘i’
font.c: In function ‘getStringGLListFT’:
font.c:530: warning: unused variable ‘h1’
font.c:530: warning: unused variable ‘w1’
font.c:530: warning: unused variable ‘h’
font.c:530: warning: unused variable ‘w’
font.c:530: warning: unused variable ‘i’
font.c:530: warning: unused variable ‘pen_y’
font.c:530: warning: unused variable ‘pen_x’
font.c: In function ‘makeGLGeometryFT’:
font.c:469: warning: ‘tdv_s’ is used uninitialized in this function
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT sys_stuff.o -MD -MP -MF ".deps/sys_stuff.Tpo" \
  -c -o sys_stuff.o `test -f 'sys_stuff.c' || echo './'`sys_stuff.c; \
then mv ".deps/sys_stuff.Tpo" ".deps/sys_stuff.Po"; \
else rm -f ".deps/sys_stuff.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT net_socket.o -MD -MP -MF ".deps/net_socket.Tpo" \
  -c -o net_socket.o `test -f 'net_socket.c' || echo './'`net_socket.c; \
then mv ".deps/net_socket.Tpo" ".deps/net_socket.Po"; \
else rm -f ".deps/net_socket.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT sound_stuff.o -MD -MP -MF ".deps/sound_stuff.Tpo" \
  -c -o sound_stuff.o `test -f 'sound_stuff.c' || echo './'`sound_stuff.c; \
then mv ".deps/sound_stuff.Tpo" ".deps/sound_stuff.Po"; \
else rm -f ".deps/sound_stuff.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT menu.o -MD -MP -MF ".deps/menu.Tpo" \
  -c -o menu.o `test -f 'menu.c' || echo './'`menu.c; \
then mv ".deps/menu.Tpo" ".deps/menu.Po"; \
else rm -f ".deps/menu.Tpo"; exit 1; \
fi
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT bumpref.o -MD -MP -MF ".deps/bumpref.Tpo" \
  -c -o bumpref.o `test -f 'bumpref.c' || echo './'`bumpref.c; \
then mv ".deps/bumpref.Tpo" ".deps/bumpref.Po"; \
else rm -f ".deps/bumpref.Tpo"; exit 1; \
fi
bumpref.c: In function ‘bumpref_create_cubemap’:
bumpref.c:65: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
bumpref.c:94: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c:95: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c:96: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c:97: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c:98: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c:99: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c: In function ‘bumpref_create_bumpmap’:
bumpref.c:284: warning: dereferencing type-punned pointer will break strict-aliasing rules
bumpref.c:286: warning: pointer targets in passing argument 3 of ‘bump2normal_HILO’ differ in signedness
bumpref.c:288: warning: pointer targets in passing argument 3 of ‘bump2normal’ differ in signedness
bumpref.c:291: warning: pointer targets in passing argument 2 of ‘glGenTextures’ differ in signedness
bumpref.c: In function ‘bumpref_setup_vp_ts_rc’:
bumpref.c:426: warning: pointer targets in initialization differ in signedness
bumpref.c:435: warning: implicit declaration of function ‘glGenProgramsNV’
bumpref.c:436: warning: implicit declaration of function ‘glBindProgramNV’
bumpref.c:437: warning: implicit declaration of function ‘glLoadProgramNV’
bumpref.c:437: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
bumpref.c:445: warning: implicit declaration of function ‘glTrackMatrixNV’
bumpref.c:447: warning: implicit declaration of function ‘glProgramParameter4fNV’
bumpref.c:472: warning: implicit declaration of function ‘glCombinerParameteriNV’
bumpref.c:473: warning: implicit declaration of function ‘glCombinerOutputNV’
bumpref.c:503: warning: implicit declaration of function ‘glFinalCombinerInputNV’
bumpref.c:429: warning: unused variable ‘s_gen_params’
bumpref.c:428: warning: unused variable ‘t_gen_params’
bumpref.c: In function ‘bump_setup_vp_rc’:
bumpref.c:730: warning: pointer targets in initialization differ in signedness
bumpref.c:735: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
bumpref.c:830: warning: implicit declaration of function ‘glCombinerInputNV’
bumpref.c:650: warning: unused variable ‘const1’
bumpref.c:649: warning: unused variable ‘const0’
bumpref.c: In function ‘bump_set_diff’:
bumpref.c:1142: warning: implicit declaration of function ‘glCombinerParameterfvNV’
bumpref.c: In function ‘bumpref_create_bumpmap’:
bumpref.c:283: warning: ‘sdata’ may be used uninitialized in this function
gcc -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2  `freetype-config --libs` `sdl-config --libs`   -o foobillard  billard3d.o billmove.o billard.o vmath.o ball.o png_loader.o table.o queue.o aiplayer.o options.o evaluate_move.o helpscreen.o textobj.o font.o sys_stuff.o net_socket.o sound_stuff.o menu.o bumpref.o -lSM -lICE -L/usr/X11R6/lib  -lGL -lGLU -lXaw -lm -lXi -lpng -lz
/usr/bin/ld: cannot find -lXaw
collect2: ld returned 1 exit status
make[2]: *** [foobillard] Error 1
make[2]: Leaving directory `/home/shaj/Gamez/foobillard-3.0a/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/shaj/Gamez/foobillard-3.0a/src'
make: *** [all-recursive] Error 1
```

then ran make install

```
Making install in src
make[1]: Entering directory `/home/shaj/Gamez/foobillard-3.0a/src'
gcc -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2  `freetype-config --libs` `sdl-config --libs`   -o foobillard  billard3d.o billmove.o billard.o vmath.o ball.o png_loader.o table.o queue.o aiplayer.o options.o evaluate_move.o helpscreen.o textobj.o font.o sys_stuff.o net_socket.o sound_stuff.o menu.o bumpref.o -lSM -lICE -L/usr/X11R6/lib  -lGL -lGLU -lXaw -lm -lXi -lpng -lz
/usr/bin/ld: cannot find -lXaw
collect2: ld returned 1 exit status
make[1]: *** [foobillard] Error 1
make[1]: Leaving directory `/home/shaj/Gamez/foobillard-3.0a/src'
make: *** [install-recursive] Error 1
```

I also noticed something during configure that it says I have no GLUT support????

:(

---

### Post by Perfect Storm on 2005-12-26
Hmmm....now I tried to build it without success, if anyone else have an idea please post. Perhaps are lib I missed? Or a flag that have to be enable that I'm not aware of? There's no help on the web-site or in the readme file :-/ Anyone who can shines some light on it?


Shaj, I can't help you with it, sorry :-/....but I know another game of the same. If you have universe enable in your source list. Open thet terminal 

```
sudo dpkg -i install billard-gl
killall gnome-panel

```

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]Hmmm....now I tried to build it without success, if anyone else have an idea please post. Perhaps are lib I missed? Or a flag that have to be enable that I'm not aware of? There's no help on the web-site or in the readme file :-/ Anyone who can shines some light on it?


Shaj, I can't help you with it, sorry :-/....but I know another game of the same. If you have universe enable in your source list. Open thet terminal 

```
sudo dpkg -i install billard-gl
killall gnome-panel

```[/QUOTE]

dpkg: error processing install (--install):
 cannot access archive: No such file or directory
dpkg: error processing billard-gl (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install
 billard-gl


:(

---

### Post by Perfect Storm on 2005-12-26
and you have enable universe in your source list?


Aghhggg sory, sory, sorry...my fault...I must be tired. It's 

sudo apt-get install billard-gl

---

### Post by shaj on 2005-12-26
[QUOTE=Artificial Intelligence]and you have enable universe in your source list?


Aghhggg sory, sory, sorry...my fault...I must be tired. It's 

sudo apt-get install billard-gl[/QUOTE]

You won't believe this...

I just did a search on Synaptics Package Manager for Billard to try and Install billard-gl...

not only did I find billard-gl there...I also found foobillard!?!

I installed both of em...

Billard-Gl is on the games menu now, but not foobillard...

so gonna look for that now...

thanks so much for all your help...

---

### Post by Perfect Storm on 2005-12-26
terminal write foobillard

By the way I've been talking to Kassetra, you need to install libxaw-dev if you want to compile it:

```

sudo apt-get install libxaw7-dev libxaw-headers checkinstall

```

now
./configure
make
sudo checkinstall

This only work if you have nvidia card

---

### Post by fred the wise on 2007-05-29
Hi guys
I'm trying to play against the computer but I can't find the way to do it..
I've read it is possible..but how?
thanks for the help..
Fred

---

### Post by fred the wise on 2007-05-29
I've done it...

---

