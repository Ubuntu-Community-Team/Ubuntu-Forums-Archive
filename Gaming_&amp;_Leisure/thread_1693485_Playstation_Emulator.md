---
title: "Playstation Emulator?"
date: 2011-02-22
forum: Gaming &amp; Leisure
---

### Post by DeviantGuy on 2011-02-22
Hello!

I am curious if their is any Playstation Emulators for Ubuntu? 
I would prefer a GUI based one rather than a Terminal based emulator. Thanks! ;)
And also, I know this is off topic but can someone please explain to me what the heck this beans thing is... Please?

---

### Post by fct on 2011-02-23
You can run pcsx reloaded for ubuntu ( [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048) ), or epsxe for windows using wine ( [http://appdb.winehq.org/objectManager.php?sClass=application&iId=649](http://appdb.winehq.org/objectManager.php?sClass=application&iId=649) ).

Beans are posts in this forum.

Edit: better link: [http://ubuntuforums.org/showthread.php?t=1647148](http://ubuntuforums.org/showthread.php?t=1647148)

---

### Post by tjwoosta on 2011-02-23
> **fct said:**
> You can run pcsx reloaded for ubuntu ( [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048) ), or epsxe for windows using wine ( [http://appdb.winehq.org/objectManager.php?sClass=application&iId=649](http://appdb.winehq.org/objectManager.php?sClass=application&iId=649) ).

Beans are posts in this forum.

Edit: better link: [http://ubuntuforums.org/showthread.php?t=1647148](http://ubuntuforums.org/showthread.php?t=1647148)

Why in wine? epsxe has a linux version that works fine ;)

---

### Post by disturbedite on 2011-02-23
if you'd like to use (and manage) plugins, i'd recommend PCSXR like fct said.
if you want less hassle (it doesn't support plugins) then i recommend pSX. (this is the playstation emulator i use).

---

### Post by ryanjude on 2011-02-23
It really made my day as I was searching for something similar xD
 
I'll go try it out later tonight, Playstation Emulator, here I come. oh, btw is that hard to set up/install? i'm new to Ubuntu, well, haven't come across it before.

---

### Post by DeviantGuy on 2011-02-24
> **disturbedite said:**
> if you'd like to use (and manage) plugins, i'd recommend PCSXR like fct said.
if you want less hassle (it doesn't support plugins) then i recommend pSX. (this is the playstation emulator i use).

pSX was the Playstation emulator I used when I was using windows. However, when I load the BIOS (Scph1001.bin) via the file explorer it just closes... suggestions?
Ryanjude, it shouldn't be too hard.

---

### Post by tjwoosta on 2011-02-24
Try running it in a terminal and see what the output is when it crashes.

---

### Post by disturbedite on 2011-02-24
> **DeviantGuy said:**
> pSX was the Playstation emulator I used when I was using windows. However, when I load the BIOS (Scph1001.bin) via the file explorer it just closes... suggestions?
are you asking about running it on windows?

---

### Post by DeviantGuy on 2011-02-24
> **disturbedite said:**
> are you asking about running it on windows?

No, it worked with some sound errors on Windows. But on Ubuntu It won't open.

---

### Post by disturbedite on 2011-02-25
> **DeviantGuy said:**
> No, it worked with some sound errors on Windows. But on Ubuntu It won't open.

run it from console and post the output.

---

### Post by honeybear on 2011-02-25
```
/usr/games/pcsx -nogui -cdfile  file
```

for xbox gamepad dfinput.cfg
```

[general]
pcsx_style      = 1
use_threads     = 1
use_analog      = 0
[pad 1]
devicefilename  = /dev/input/js1
minzero = -250
maxzero = 250
event_l2       = 
event_r2       = 
event_l1       = B0P4
event_r1       = B0P5
event_triangle = B0P3
event_circle   = B0P1
event_cross    = B0P0
event_square   = B0P2
event_select   = B0P14
event_lanalog  = 
event_ranalog  = 
event_start    = B0P6
event_up       = B0P10
event_right    = B0P13
event_down     = B0P11
event_left     = B0P12
event_lanax    = 
event_lanay    = 
event_ranax    = A0P4+
event_ranay    = A0P5-
[macro 1]
event_launch  = 
events        =
interval      =
[macro 2]
event_launch  = 
events        =
interval      =
[macro 3]
event_launch  =
events        =
interval      =
[pad 2]
devicefilename  = /dev/input/js2
minzero = -250
maxzero = 250
event_l2       = A1P2-
event_r2       = A1P5-
event_l1       = B1P4
event_r1       = B1P5
event_triangle = B1P3
event_circle   = B1P1
event_cross    = B1P0
event_square   = B1P2
event_select   = A1P0-
event_lanalog  = ???
event_ranalog  = ???
event_start    = B1P6
event_up       = B1P10
event_right    = B1P13
event_down     = B1P11
event_left     = B1P12
event_lanax    = ???
event_lanay    = ???
event_ranax    = ???
event_ranay    = ???
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =

```


if not working:
[http://forums.debian.net/viewtopic.php?f=16&t=51266](http://forums.debian.net/viewtopic.php?f=16&t=51266)
but pcsx-df is far better

---

