---
title: "NWN Sound and Metallic Robes/Cloaks"
date: 2010-08-20
forum: Gaming &amp; Leisure
---

### Post by wereguy2 on 2010-08-20
I am sure this will have been asked before, but I am pretty stuck, and have been for months.
Firstly, sound doesn't work with my copy of NWN, run on Kubuntu 9.10. I have tried a few different methods that seem to have worked for others, such as removing ./lib from.. somewhere in the openy file:
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=alsa
export XCURSOR_PATH=`pwd`
export XCURSOR_THEME=nwmouse
export LD_PRELOAD=./nwmouse.so

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@
```Secondly, all robes and cloaks, as well as wings and even whole creatures (for example, the Satyr), show up as being metallic. I have tried turning Environment Mapping off ingame, and it hasn't worked. I also tried turning it off altogether using driconf, but the option didn't even show up there.
I have an Intel 865G chipset.

Any help would be appreciated.

Also, the Bioware NWN forums have been shut down, so no, I can't ask there.

---

