---
title: "Nautilus transparent background patch"
date: 2011-03-04
forum: Desktop Environments
---

### Post by pr3ddi on 2011-03-04
here you go ... a nautilus transparent background patch for everone who is not afraid to compile nautilus from source :-)

what you will get:
- a transparent nautilus desktop window in compiz, which has the usual desktop integration (icons and context menu)
- a working wallpaper plugin, that can be set to show a different wallpaper on every screen
- you can even use mplayer to play a video on your background

how it's done:
- the nautilus desktop window is modified to render a transpart background, if a composited screen is detected
- window type is changed from _NET_WM_WINDOW_TYPE_DESKTOP to _NET_WM_WINDOW_TYPE_NOTIFICATION
- window is set to be keept below all other windows and the mouse wheel event is proxied to the root window

the patch was developed for nautilus 2.28.1 (Ubuntu 9.10) first and then applied to nautilus 2.30.1 (Ubuntu 10.04)
the only difference in 2.28.1 is that there is one more row (below set_image_properties) in the original eel-background.c

please follow the detailed instructions in the 98_transparent-background.txt file

have a nice day

pr3ddi

---

