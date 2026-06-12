---
title: "delete key not working correctly under 8.10"
date: 2008-12-07
forum: General Help
---

### Post by ekarni on 2008-12-07
All,

Clean install of 8.10 Intrepid fails to properly recognize the delete key everywhere - tested in the terminal, firefox, open office, gedit.  In terminal, pressing delete causes the cursor to flash, rather than removing the selected character.  This was working fine before the upgrade, so I don't think it is a simple bad key hardware problem.  Strangely, pressing alt+del does delete the character, but only with the right alt key, not the left.  

Things I've tried (ref [http://ubuntuforums.org/showthread.php?t=948822&highlight=delete+key]("http://ubuntuforums.org/showthread.php?t=948822&highlight=delete+key"):
-Remapping keyboard (system->preferences->keyboard) including generic Evdev-managed, generic 101,  generic 104, and a close match to the exact model (it's a HP 5184 USB multimedia keyboard).  Tried deleting default and recreating it, no luck.
-Doing same by reconfiguring xserver.  (Bad idea, corrupted graphics and had to revert to old xorg.conf)
-Changing mappings using xmodmap.  tried keycode 107 = Delete and KP_Delete  Should this take effect immediately, or do I need to do something similar to sourcing a .cshrc file?  (I've been assuming it will take effect immediately)

Any more ideas?  Thanks!


Here's my xev output for a plain del press:
```
FocusOut event, serial 33, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967176 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

For right alt+del (acts like plain del should):
```
KeyPress event, serial 30, synthetic NO, window 0x3200001,
    root 0x188, subw 0x3200002, time 3797673, (46,49), root:(52,831),
    state 0x10, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x3200001,
    root 0x188, subw 0x3200002, time 3797801, (46,49), root:(52,831),
    state 0x90, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XmbLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x188, subw 0x3200002, time 3797905, (46,49), root:(52,831),
    state 0x90, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x188, subw 0x3200002, time 3797961, (46,49), root:(52,831),
    state 0x90, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

For del on the numeric keypad with numlock off:
```
KeyPress event, serial 30, synthetic NO, window 0x3200001,
    root 0x188, subw 0x3200002, time 3653681, (47,41), root:(120,118),
    state 0x0, keycode 91 (keysym 0xff9f, KP_Delete), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3200001,
    root 0x188, subw 0x3200002, time 3653737, (47,41), root:(120,118),
    state 0x0, keycode 91 (keysym 0xff9f, KP_Delete), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

xmodmap -pke | grep -in delete:
```

84:keycode  91 = KP_Delete KP_Decimal KP_Delete KP_Decimal KP_Delete KP_Decimal
100:keycode 107 = Delete Delete Delete Delete Delete
112:keycode 119 = Delete NoSymbol Delete NoSymbol Delete


```

---

