---
title: "KDE Keyboard mouse bugs"
date: 2010-11-20
forum: Desktop Environments
---

### Post by ryadav on 2010-11-20
This just started happening, i've been using kubuntu 10.10 without an issues for a while.

problem one my mouse button click will just stop working, i am unable to focus on a window, close it etc.

problem two my 'up' key no longer works, if i run xev this is the ouput, the key event is getting noticed but the output is odd?

btw i've tried using a 2nd keyboard, plugged into a seperate usb port, same problem.

FocusOut event, serial 34, synthetic NO, window 0x4000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x4000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   4294967168 0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x4000001,
    root 0x15a, subw 0x0, time 1254472, (-1740,-199), root:(0,819),
    state 0x10, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

