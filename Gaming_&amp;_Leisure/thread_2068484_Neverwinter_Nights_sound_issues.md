---
title: "Neverwinter Nights sound issues"
date: 2012-10-09
forum: Gaming &amp; Leisure
---

### Post by stackmanpf77 on 2012-10-09
I am having a great deal of difficulty getting sounds active in NWN (platinum CD install)...
I've altered the nwn run script in every way I've found on this, and many other forums, all to no avail.
I Did get it working for about 12 hours with the addition of the 

export SDL_AUDIODRIVERS=alsa

command line, but did a system restart and it has gone kaput.
Nothing I have tried since has had any effect whatsoever besides turning my hair grey.

Currently, my nwn run script reads as - 

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
#export SDL_AUDIODRIVERS=alsa

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@

and nothing sound-wise...
(sound aside, game runs flawlessly, no high res screen flutter/flicker, no mouse lag, movies work (sans sound)

I've tried the ravage installer, leech's guide, and a variety of other potential fixes I've found all to no avail.

any help would be appreciated.

---

### Post by IamDUFF on 2012-10-15
I'm having the same problems.
What's odd though, is I've gotten it working on Gentoo, and Ubuntu before.
My only thoughts are, maybe Ubuntu Studio (and other odd derivatives) has something missing that the vanilla install has, or that the 12.04.1 update changed something.
I've got ia32 and multiarch so I'm just not too sure. Maybe I missed some package on the install disk.

(edit: I'm not sure why this is labeled as solved. =P crazy mods.)

---

### Post by stackmanpf77 on 2012-10-18
haha, nope it was me not the mods that marked it as solved :)

my sound problems merely came from my sound preferences magically resetting themselves to defaults when i did a reboot :/

once I'd switched them back to what they shoulda been, it fired up sweet-as...

/embarrassed

---

