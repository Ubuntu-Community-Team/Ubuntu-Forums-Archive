---
title: "Pressing &lt;Alt&gt; takes focus from window"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by splab on 2007-10-04
When I'm in a window and press <Alt> the window loses focus and the next key always gets send to compiz. This is really annoying since I need <Alt>+1 - <Alt>+0 for irssi to change windows. Anyone knows what I have to disable to get this behavior to stop?

(This also happens in any other program, I can't press <Alt>+f to get file menu in firefox for instance). 

From xev when I press <Alt>:
FocusOut event, serial 27, synthetic NO, window 0x2a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 27, synthetic NO, window 0x2a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


Any help would be much appreciated.

---

