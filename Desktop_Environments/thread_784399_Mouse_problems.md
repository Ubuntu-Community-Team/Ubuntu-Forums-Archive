---
title: "Mouse problems"
date: 2008-05-06
forum: Desktop Environments
---

### Post by jimtb on 2008-05-06
I just upgraded to Hardy. Almost everything seems to be working pretty good except my mouse. After the upgrade, a click from any of my mouse buttons registers as two clicks.

Here's the output from xev after a simple click:
```
ButtonPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 2013981, (93,89), root:(98,141),
    state 0x10, button 1, same_screen YES

ButtonPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 2013981, (93,89), root:(98,141),
    state 0x110, button 1, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 2014045, (93,89), root:(98,141),
    state 0x110, button 1, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x40, subw 0x0, time 2014045, (93,89), root:(98,141),
    state 0x10, button 1, same_screen YES
```

Due to this problem I can't use any context menus, right click etc. 

**Edit:** Solved by reconfiguring the xserver-xorg package.

---

