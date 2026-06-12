---
title: "Alt and AltGr keys not detected."
date: 2010-03-01
forum: Desktop Environments
---

### Post by pangel on 2010-03-01
Hi, I cannot use my AltGr key to type characters such as { } \ / #. 
Alt is not detected either.

OS:               ** Ubuntu 9.10**
Laptop:            ** Asus M70Sa**
Keyboard:          ** french layout**
Keyboard config:** asus laptop keyboard + french alternative**

Here is the output from xev (X events) :

**Left Ctrl**
```
KeyPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x9e, subw 0x4200002, time 3000929, (19,37), root:(25,88),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4200001,
    root 0x9e, subw 0x4200002, time 3001078, (19,37), root:(25,88),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 36, synthetic NO, window 0x4200001,
    mode NotifyGrab, detail NotifyAncestor
```

**Alt**```
KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 36, synthetic NO, window 0x4200001,
    mode NotifyGrab, detail NotifyAncestor
```

**Alt Gr**
```
KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  
```

---

### Post by labinnsw on 2010-03-08
I recommend Keytouch and Keytouch Editor (KDE apps that are included in the repositories and are compatible with Gnome.)

---

