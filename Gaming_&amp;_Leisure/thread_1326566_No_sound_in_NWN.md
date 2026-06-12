---
title: "No sound in NWN"
date: 2009-11-14
forum: Gaming &amp; Leisure
---

### Post by Duskao on 2009-11-14
Probably a pulseaudio issue I'm sure, but maybe someone knows about this. I'm getting no sound in Neverwinter Nights.

---

### Post by Melcar on 2009-11-14
Open the nwn binary file with a text editor and remove the *./lib:* entry.  The file should look something like this after editing:

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@

```

---

### Post by Duskao on 2009-11-14
Thx

---

