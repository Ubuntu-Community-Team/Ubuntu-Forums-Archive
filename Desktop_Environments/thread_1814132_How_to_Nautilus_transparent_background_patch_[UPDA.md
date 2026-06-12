---
title: "How to: Nautilus transparent background patch [UPDATED]"
date: 2011-07-29
forum: Desktop Environments
---

### Post by pr3ddi on 2011-07-29
here you go ... a nautilus transparent background patch for everone who is not afraid to compile nautilus from source

what you will get:
- a transparent nautilus desktop window in compiz, which has the usual desktop integration (icons and context menu)
- a working wallpaper plugin, that can be set to show a different wallpaper on every screen
- you can even use mplayer to play a video on your background

how it's done (old):
- the nautilus desktop window is modified to render a transpart background, if a composited screen is detected
- window type is changed from _NET_WM_WINDOW_TYPE_DESKTOP to _NET_WM_WINDOW_TYPE_NOTIFICATION
- window is set to be keept below all other windows and the mouse wheel event is proxied to the root window

the [old version of the patch]("http://ubuntuforums.org/showthread.php?t=1699841") was developed for nautilus 2.28.1 (Ubuntu 9.10) first and then applied to nautilus 2.30.1 (Ubuntu 10.04)

_**how it's done (new):**_
 - the nautilus desktop window is modified to render a transpart background, if a composited screen is detected
 - the new, improved version does not need to change the window type, it  looks like gnome supports a transparent root window now. old code was  removed.
- a detection routine has been added, to support the change of the  "composited" mode of the desktop, switching from compiz to metacity and  back is being detected
- does not need the "sleep" workaround on startup, like the old version
- tested with 10.04 and 11.04

please follow the detailed instructions in the 98_transparent-background-v2.txt file

have a nice day

pr3ddi

---

### Post by qos on 2011-07-29
Thank you very very much! Great patch!

Waited long time before i got it for 2.32.2

---

### Post by fguille on 2011-07-30
Thanks for this V2. Upgraded Nautilus Elementary 2.32.2 with this new version on 11.4 ok.
Can't rename a desktop item with another window visible on workspace (with follow mouse focus), but ok on empty workspace, so really minor thing, much better overall beahaviour than V1, thanks again !

---

### Post by rocketman221 on 2011-08-14
Thanks
It works great on Ubuntu 11.04 in gnome classic mode.

---

### Post by Zhono on 2012-09-22
Will this work on 12.04?

---

### Post by zombifier25 on 2012-09-23
> **Zhono said:**
> Will this work on 12.04?

Doubt it. The last version tested was Nautilus 2.x. Nautilus has reached version 3.4 now, which uses GTK+3, along with one heck of changes.

---

