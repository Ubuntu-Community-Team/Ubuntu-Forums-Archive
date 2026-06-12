---
title: "Multimedia key prev doesn't work"
date: 2008-12-28
forum: General Help
---

### Post by prokaryot on 2008-12-28
This closed thread is still valid:
[http://ubuntuforums.org/showthread.php?t=870812](http://ubuntuforums.org/showthread.php?t=870812)

> The XF86AudioPrev can be set to any action in Keyboard Shortcuts, but will not respond. If I set it directly as a hotkey in Exaile (possibly other apps too but not tested), it works. This was an issue with later updates in Hardy and still with Intrepid alpha 3.

I use xbindkeys to assing commands, all worked except key XF86AudioPrev.
xev output is:
> 
FocusOut event, serial 30, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


I guess it's just focusing and unfocusing window

---

