---
title: "UT2004 - Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:1.0&quot;."
date: 2007-03-10
forum: Gaming &amp; Leisure
---

### Post by adamr on 2007-03-10
I have a recently new install of Edgy, and am running XGL/Beryl. I've installed UT2004 from my original DVD, and patched it up to version 3355, but the game will not run for me.

I get the splash screen, and it tries to start but the console reads..
> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
WARNING: ALC_EXT_capture is subject to change!


I'm running an ati 9600XT, any ideas folks?

---

### Post by Perfect Storm on 2007-03-10
Try turn off Beryl before strating ut2004

---

### Post by adamr on 2007-03-12
I thought I'd better just check in and say that yes, just starting a normal Gnome session fixed it no problem.

Not being a Linux fiend (yet!), can I assume it was because by default the machine/game is set to run on display 0:0, and instead had to try 0:1 because Beryl was running in GL and had already 'claimed' that display?

I've a feeling I may be a long way wide of the mark :)

---

