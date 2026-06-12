---
title: "Shift key not working after login"
date: 2008-04-03
forum: Desktop Environments
---

### Post by mfbaker on 2008-04-03
Hi, 
I'm having a problem where when I login to my normal Gnome/X session the shift key doesn't work. xev registers the shift key, but not shift+(letter). It works on the login screen and in the failsafe Gnome session though (which is why I can have caps here).

I've looked at the rcconf program, but I don't know if I can turn everything off safely and keep turning things on until the shift key stops registering again. Below is what xev gives me on the left and then right shift keys. On the failsafe session it maps to keys 50 and 62, so I don't know what is getting in the way.

Any help is appreciated, I can get you more information from either session if it'll be useful.

```
FocusOut event, serial 31, synthetic NO, window 0x4400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x4400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```

---

### Post by mfbaker on 2008-04-03
Okay, this is a little bit more weird, when I push down one shift key then the other, then release the first key I pressed shift is on:

```
FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   4   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x5d, subw 0x0, time 377340099, (422,-262), root:(429,325),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by acscherp on 2008-06-06
I have the same problem on ubuntu. In the GDM login screen, the shift key works, but after logging in, xev gives me a 'focusout' event instead of a regular shift key press. Weird!!

---

### Post by kaurman on 2008-07-03
Hi!

Try this:

[http://ubuntuforums.org/showthread.php?t=785029](http://ubuntuforums.org/showthread.php?t=785029)

---

