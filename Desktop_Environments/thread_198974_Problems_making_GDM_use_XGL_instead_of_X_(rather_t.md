---
title: "Problems making GDM use XGL instead of X (rather than XGL as [Desktop Entry])"
date: 2006-06-18
forum: Desktop Environments
---

### Post by irrlicht on 2006-06-18
Hey folks, i'm having problems using XGL instead of X for GDM. 
I installed XGL/Compiz and it works fine when starting it over GDM's Session-Menu (i.e., when having a [Desktop Entry] for it). But i do not want to do that any more, because it makes my shutdown/restart-buttons disappear.

So I wanted to give the other method a shot, i.e. make GDM use XGL rather than X.
I added this to my /etc/X11/gdm/gdm.conf-custom:
```
[servers]
0=inactive
1=Xgl

# Definition of the xgl X server.
[server-Xgl]
name=Xgl
command=/usr/bin/Xgl :1 -ac -accel xv:pbuffer -accel glx:pbuffer
flexible=true
chooser=false
handled=true
priority=0 
```

This leads to GDM not starting any more. I see that black-white background coming up and dissapearing three times, before the usual GDM-starting-failure-message comes up (without giving me any usable errors as far as I can tell (the offered X11-error log has no EE-entries whatsoever).

When I start XGL via the console (sudo, while GDM is *not* running), it seems to work: after a while, the screen is painted, but -quite naturally- gnome is missing. 
So appearently XGL should work, why does GDM not like it?

Does anyone have a clue what I am missing here?

---

