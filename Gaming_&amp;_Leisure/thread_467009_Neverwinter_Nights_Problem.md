---
title: "Neverwinter Nights Problem"
date: 2007-06-07
forum: Gaming &amp; Leisure
---

### Post by Virgilius on 2007-06-07
Ok, I have installed NWN1 on my Ubuntu box and installed everything from Gold Edition and Hordes of the Underdark to be at 1.68 to play online, but time and time again, I would get a segmentation fault or when it came to create a new character, NWN would boot me out of it when I clicked. Anything that could help?

---

### Post by rockytriton on 2007-06-07
what are you using to play NWN on linux?

---

### Post by Virgilius on 2007-06-07
Ubuntu Edgy/Win XP dual-boot
GeForce 6200
1Gig RAM
Processor (CPU) unknown
NWN: Gold Ed and Linux client binaries (DL-ed from site, Bioware)
Anything else?

---

### Post by calgarystevens on 2007-06-07
The only thing I can think of are:
1. Did you delete the files out of the 'override' directory as per the patch instructions (probly did, but a shot in the dark)
2. I found my sound really crackly with the default SDL library (probly old as the hills) so I made a copy of my nwn executable first, then I edited it to look this: 

```

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=/usr/lib:./miles:$LD_LIBRARY_PATH

cd /home/ed/games/nwn
./nwmain $@

```

Now it uses the recent SDL library in Ubuntu and seems to work great for me (Diamond Edition btw)

---

### Post by Virgilius on 2007-06-08
> 1. Did you delete the files out of the 'override' directory as per the patch instructions (probly did, but a shot in the dark) Yep, did it.

> 2. I found my sound really crackly with the default SDL library My sound was quite okay, nothing wrong. It was what I've written beforehand.

---

