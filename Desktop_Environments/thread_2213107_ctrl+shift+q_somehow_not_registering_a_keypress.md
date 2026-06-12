---
title: "ctrl+shift+q somehow not registering a keypress?"
date: 2014-03-24
forum: Desktop Environments
---

### Post by jordansamuels on 2014-03-24
I am running a recently updated Ubuntu 13.10, and it appears that ctrl+shift+q is broken somehow. When I run xev and hit ctrl+shift+q, I do see a keypress event, like I would for other keys.  Here is xev when I hit ctrl+shift+q and then ctrl+shift+w:
[INDENT][FONT=courier new]
[/FONT]KeyPress event, serial 40, synthetic NO, window 0x1000001,
    root 0x288, subw 0x0, time 34111826, (128,79), root:(135,656),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 40, synthetic NO, window 0x1000001,
    root 0x288, subw 0x0, time 34111841, (128,79), root:(135,656),
    state 0x4, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


FocusOut event, serial 40, synthetic NO, window 0x1000001,
    mode NotifyGrab, detail NotifyAncestor


FocusOut event, serial 40, synthetic NO, window 0x1000001,
    mode NotifyUngrab, detail NotifyPointer


FocusIn event, serial 40, synthetic NO, window 0x1000001,
    mode NotifyUngrab, detail NotifyAncestor


KeymapNotify event, serial 40, synthetic NO, window 0x0,
    keys:  4294967176 0   0   0   32  0   4   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


KeyPress event, serial 40, synthetic NO, window 0x1000001,
    root 0x288, subw 0x0, time 34112631, (128,79), root:(135,656),
    state 0x5, keycode 25 (keysym 0x57, W), same_screen YES,
    XLookupString gives 1 bytes: (17) ""
    XmbLookupString gives 1 bytes: (17) ""
    XFilterEvent returns: False


KeyRelease event, serial 40, synthetic NO, window 0x1000001,
    root 0x288, subw 0x0, time 34112763, (128,79), root:(135,656),
    state 0x5, keycode 25 (keysym 0x57, W), same_screen YES,
    XLookupString gives 1 bytes: (17) ""
    XFilterEvent returns: False


[/INDENT]

This is true when I use the default Ubuntu window manager, or i3, or Enlightenment.  Strangely enough, ctrl+shift+q did register when I tried to bind it to a custom key in Gnome settings -> keyboard (although it didn't end up working; Gnome keyboard custom commands are pretty well known to be brittle and usually break or me).

Any help would be greatly appreciated.

Thanks,
Jordan

P.S. This is my first help request on these forums, so any criticism/tips/advice on how to post are very welcome.

---

