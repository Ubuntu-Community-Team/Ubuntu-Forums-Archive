---
title: "Ut2k4"
date: 2005-04-29
forum: Gaming &amp; Leisure
---

### Post by chz on 2005-04-29
installed unreal tournament 2004 fine. run the game...i get the intro splash screen fine...then closes. getting this message

=====================================
$ ./ut2004
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
=====================================

have no idea what to do. any hints please?

---

### Post by odix on 2005-04-29
is DRI working correctly ???
type **glxinfo | grep "direct render"** in console or terminal. it should give:
direct rendering: Yes
if No you have to configure your gfx card correctly.

odiX

---

### Post by jdodson on 2005-04-29
try this guide: [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

---

