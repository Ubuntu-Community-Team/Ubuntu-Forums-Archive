---
title: "small Q-key does not work"
date: 2009-08-06
forum: Desktop Environments
---

### Post by apeus711 on 2009-08-06
hej,

suddenly my small "Q" does not work under gnome. it is ok on KDE, xfce, etc.
i tried to change the keyboard layouts and keyboard-types via the gnome keyboard-layout application (i'm on an acer 7520 notebook).
i ran xev and pressed first the "sane" a key and then the "insane" (small) Q key.
unfortunately i cannot find anything useful from this piece of information.
btw, "shift+(small)Q" works fine.

can anybody help me :) ?

```

KeyPress event, serial 35, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 4970385, (166,-1), root:(837,82),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 4970491, (166,-1), root:(837,82),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

FocusOut event, serial 35, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 35, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 35, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  60  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

```

---

### Post by apeus711 on 2009-08-09
bump

---

