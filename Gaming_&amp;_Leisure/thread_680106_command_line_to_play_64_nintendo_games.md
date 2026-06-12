---
title: "command line to play 64 nintendo games ?"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-01-27
Hello, 
I just tried freevo and having nintendo 64, runing on it with :

like this
	('Tux Racer', '/etc/freevo/games/tuxracer',
                ('GENERIC', '/usr/games/tuxracer', '', '', [ 'tux' ] )) 
some code. 

Is there a nice emulator for snes64 that runs with freevo config ?
(I hope one could understand)

mupen64 is with gui.

Has sbdy freevo/mythtv working with nintendo 64 games ?
thx

---

### Post by acoustibop on 2008-01-27
I would have thought Mupen64 supports terminal commands, frenchn00b - every other emulator I've come across does, even if they have GUIs.

---

### Post by DoktorSeven on 2008-01-27
Get the source code for mupen64, you can compile a version without the GUI (mupen64_nogui, I think it was called).

---

### Post by frenchn00b on 2008-02-15
I found this how to but get error:

```
$ make
gcc -DX86 -O3 -fexpensive-optimizations -fomit-frame-pointer -funroll-loops -ffast-math -fno-strict-aliasing -mcpu=athlon -Wall -pipe `freetype-config --cflags` `sdl-config --cflags` -c -o blight_input/SDL_ttf.o blight_input/SDL_ttf.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
blight_input/SDL_ttf.c:51:38: freetype/internal/ftobjs.h: No such file or directory
blight_input/SDL_ttf.c: In function `TTF_OpenFontIndexRW':
blight_input/SDL_ttf.c:278: error: dereferencing pointer to incomplete type
make: *** [blight_input/SDL_ttf.o] Error 1


```

>  no gui

 Nintendo: N64
[edit]
Mupen 64

Homepage: [http://mupen64.emulation64.com/](http://mupen64.emulation64.com/)

Version: 0.5

You must compile Mupen from source because the binary versions do not include the nogui version.

Download Mupen source by running wget [http://mupen64.emulation64.com/files/0.5/mupen64_src-0.5.tar.bz2](http://mupen64.emulation64.com/files/0.5/mupen64_src-0.5.tar.bz2). Then extract the source.

Configure Mupen with ./configure

    note: you can not remotly do this, due to GTK initialization checking. Make sure you're running this within X. 

libSDL-devel is required to compile Mupen. See [http://www.libsdl.org/](http://www.libsdl.org/).

Mupen64 0.5 comes with a bug which results in the nogui version not compiling. To fix this, edit main/main.c and insert the following at the beginning of the file:

#include <dirent.h>
#include <sys/stat.h>

Compile the Mupen nogui Version with:

make mupen64_nogui
make
make install
make install mupen64_nogui

    note: install / redundant commands are only needed if you want application/plugins/etc put into a shared area for you. 

Now you need the MUPEN Plugins. You can also compile them (the normal "make" command above made them for you) or get them within the binary distribution of the Mupen Webpage (the latter is much easier and recommended). Grab the latest zip of the compiled applicaiton (not the source, linked above) and there is a plugin's directory in that.

Create a config file to use with Mupen. An example file follows:

mupen64.conf

[Default]
Gfx Plugin = /usr/emulators/n64/bin/plugins/Glide64.so
Audio Plugin = /usr/emulators/n64/bin/plugins/jttl_audio.so
Input Plugin = /usr/emulators/n64/bin/plugins/blight_input.so
RSP Plugin = /usr/emulators/n64/bin/mupen64_hle_rsp_azimer.so
Fullscreen = true
Emulation Mode = 2
No Ask = true

    note: put this file where the mupen64_gui application is executed from. 

Add a new player in MythGame's setup:

Player Name: N64
Type: N64
Command: mupen64_nogui
Rom Path: /usr/emulators/n64/roms


---

