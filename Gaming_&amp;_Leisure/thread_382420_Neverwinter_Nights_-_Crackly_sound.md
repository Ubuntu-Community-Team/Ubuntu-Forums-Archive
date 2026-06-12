---
title: "Neverwinter Nights - Crackly sound"
date: 2007-03-12
forum: Gaming &amp; Leisure
---

### Post by fearpi on 2007-03-12
That's pretty much it, really. I get crackly sound when I play NWN on edgy. Any ideas?

---

### Post by Sandlst on 2007-03-12
Ive had trouble with this before because the sdl library that was being used was biowares own, instead of the ubuntu one, which works better. To change this open up the nwn file in your Never Winter Nights directory with a text editor, find the line ```
export LD_LIBRARY_PATH= ./lib:./miles: $LD_LIBRARY_PATH
```and change it to ```
export LD_LIBRARY_PATH= ./miles: $LD_LIBRARY_PATH
```then try launching it.  Good luck, post back if you have any problems.

---

### Post by fearpi on 2007-03-12
I had followed that same train of thought before by changing the symbolic links in nwn/lib/ to point to the SDL libraries in /usr/lib/. It did not alleviate the crackling. I just tried your method, but it still continues to crackle. Any other ideas?

---

### Post by fearpi on 2007-03-12
Well, I solved it. I removed libsdl1.2debian-alsa and installed libsdl1.2debian-oss .

---

### Post by Alterios on 2007-05-11
Code:

export LD_LIBRARY_PATH= ./miles: $LD_LIBRARY_PATH

should read

Code:

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

no space between PATH= and ./miles

---

### Post by fearpi on 2007-05-11
Does that actually make a difference?

---

### Post by Slingshot on 2007-08-10
> **Alterios said:**
> Code:

export LD_LIBRARY_PATH= ./miles: $LD_LIBRARY_PATH

should read

Code:

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

no space between PATH= and ./miles

Hi guys, thanks for the tip, this fixed up my neverwinter nights sound/music stutter , but it also stop the movies (which I could see, but not hear before changing the script. No big loss as they didnt work under vista either). Any idea's?

SS

---

### Post by elkanguro on 2007-09-26
> **Sandlst said:**
> Ive had trouble with this before because the sdl library that was being used was biowares own, instead of the ubuntu one, which works better. To change this open up the nwn file in your Never Winter Nights directory with a text editor, find the line ```
export LD_LIBRARY_PATH= ./lib:./miles: $LD_LIBRARY_PATH
```and change it to ```
export LD_LIBRARY_PATH= ./miles: $LD_LIBRARY_PATH
```then try launching it.  Good luck, post back if you have any problems.

Thanks man, it helps:)

---

### Post by Gillen on 2007-09-26
Hi All,

If this is of interest I fix my install of NWN HotU SoU as follows.

To fix sound

---------------------------------------------------------

apt-get install libsdl1.2debian-all


now edit the nwn script to look like this:


#!/bin/sh
# change to the nwn directory
cd $(dirname $0)
# set enviroment variables
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=esd
# set library search path
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
# fire up the game
./nwmain $@

-----------------------------------------------------

I picked this up from the Bioware Forum, hope it helps.

Steven.

---

### Post by Marran77 on 2009-12-11
Thanks, this really helped!

---

