---
title: "NWN installer problem"
date: 2009-07-24
forum: Gaming &amp; Leisure
---

### Post by punia1979 on 2009-07-24
*Hi everybody, I have downloaded installer for Neverwinter Nights*  ([I]nwn_129_final.run)[I] I have my linux copy of the game (2cd edition) and when I am trying to install the game it is keep on saying that I have no CDROM mounted... I was trying to point onto my CDROM location

export SETUP_CDROM=/media/cdrom0

after then I have typed in:

sh [/I][/I][I]nwn_129_final.run

installer runs ok, but when I hit install it is saying "please instert CD1"

any solution for this???:confused:
[/I]**

---

### Post by linuxguymarshall on 2009-07-24
I have no idea what you are saying so I shall give a generic piece of advice. Mount both discs before you start the install.

---

### Post by punia1979 on 2009-07-24
> **linuxguymarshall said:**
> I have no idea what you are saying so I shall give a generic piece of advice. Mount both discs before you start the install.

how to hell I mount 2 cd's? I have only one DVD in my laptop :D thats the original game on 2 cd's

---

### Post by punia1979 on 2009-07-24
ok I have sort out installation process but now when I want to run the game I am getting this info:

Fatal signal: Segmentation Fault (SDL Parachute Deployed)

!!!

---

### Post by oldrocker99 on 2009-07-24
You have to have the best available drivers for your graphics chip your laptop has; that's almost always what a Segmentation Fault results from. OpenGL has to be enabled. Here's my nwn file (movies are not enabled).


#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
#export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@

Note that I have copied the export LD_LIBRARY_PATH line in the file and have commented out the default line, the one that doesn't work.

This may just get you going. Hope so. Reply if needed. I love this game and have been playing it since it came out.

:guitar:

---

### Post by punia1979 on 2009-07-25
Thanx very much Your solution was working mate ;) I really appreciate Your help

---

### Post by punia1979 on 2009-07-25
my happiness was very short because when I start new game I am getting info that I cant create new character because the game was created using newer resources... how can I apply the path? and how can I check what version I have now?

---

### Post by punia1979 on 2009-07-25
ok I have sort this out just installed path 1.69 :) thanx for help anyways huys ;)

---

### Post by punia1979 on 2009-07-25
avesome RPG by the way...first time I play this.... any ports for Fallout?

---

