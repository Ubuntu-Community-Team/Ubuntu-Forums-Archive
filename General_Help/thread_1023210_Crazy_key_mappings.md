---
title: "Crazy key mappings"
date: 2008-12-27
forum: General Help
---

### Post by gerundi11 on 2008-12-27
I'm experiencing a rather weird problem: the XF86AudioStop key seems to lower the volume. I'm pretty sure I have not set this anywhere: I've checked the shortcut keys in the XFCE Settings Manager - no commands associated with this key. I have also checked the xev output while pressing the key; here is the dump:
FocusOut event, serial 34, synthetic NO, window 0x3600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  68  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
This one shows instead of the usual KeyPress and KeyRelease events...
This problem is rather annoying and I would appreciate any help to stop this weird behaviour of the key.

---

### Post by gerundi11 on 2008-12-27
Anyone got an idea???

---

