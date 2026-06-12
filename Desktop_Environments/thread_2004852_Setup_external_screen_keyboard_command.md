---
title: "Setup external screen keyboard command"
date: 2012-06-16
forum: Desktop Environments
---

### Post by Lovegain on 2012-06-16
Hi.

On my Lenovo IdeaPad S205 - which has been a nightmare from the start - I like to plug in an external screen via VGA. According to specifications, and keyboard symbols, the keyboard command for that is Fn+F3. This however has no effect.

How can I bind the combination to switching screen setup?

xev output for Fn+F3 follows:

[SIZE=1]```
FocusOut event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           32  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 33, synthetic NO, window 0x4c00001,
    root 0xa6, subw 0x0, time 41064877, (15,-17), root:(1116,35),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   2   0   0   0   0   0   0   0   0   0   0   0   
           32  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xa6, subw 0x0, time 41064881, (15,-17), root:(1116,35),
    state 0x40, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xa6, subw 0x0, time 41064889, (15,-17), root:(1116,35),
    state 0x40, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0xa6, subw 0x0, time 41065452, (15,-17), root:(1116,35),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```[/SIZE]

---

