---
title: "Rogue keyboard shortcut ruining my terminal experience"
date: 2009-03-15
forum: General Help
---

### Post by montooner on 2009-03-15
Hey. <up arrow> is being replaced by <take screenshot>. I can't go back up my history of terminal cmds, and it's KILLING me. I've disabled all key shortcuts in the system props and the terminal props.  If it helps, my computer's effectively freshly reformatted; old as hell, but whatevs. Any idea how I can kill this bugger? Thanks.

UPDATE: I ran xev and it gives me some really weird output.  Add comments for explanation:

```


**<<just some prep>>**

PropertyNotify event, serial 18, synthetic NO, window 0x2e00001,
    atom 0x120 (_NET_WM_STATE), time 6670738, state PropertyNewValue

KeyRelease event, serial 18, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6670764, (534,537), root:(612,633),
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
    XLookupString gives 1 bytes: (0d) "
"
    XFilterEvent returns: False

PropertyNotify event, serial 25, synthetic NO, window 0x2e00001,
    atom 0x15b (_NET_WM_ICON_GEOMETRY), time 6670820, state PropertyNewValue

PropertyNotify event, serial 32, synthetic NO, window 0x2e00001,
    atom 0x187 (XKLAVIER_STATE), time 6670869, state PropertyNewValue

**press left**
KeyPress event, serial 33, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6673652, (534,537), root:(612,633),
    state 0x10, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6673764, (534,537), root:(612,633),
    state 0x10, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**press right**
KeyPress event, serial 33, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6674220, (534,537), root:(612,633),
    state 0x10, keycode 116 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6674324, (534,537), root:(612,633),
    state 0x10, keycode 116 (keysym 0xff54, Down), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**press down**
KeyPress event, serial 33, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6674756, (534,537), root:(612,633),
    state 0x10, keycode 114 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x2e00001,
    root 0x80, subw 0x0, time 6674852, (534,537), root:(612,633),
    state 0x10, keycode 114 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**press up.  WTF?**
FocusOut event, serial 33, synthetic NO, window 0x2e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x2e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967168 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 33, synthetic NO, window 0x2e00001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 33, synthetic NO, window 0x2e00001,
    atom 0x15b (_NET_WM_ICON_GEOMETRY), time 6677255, state PropertyNewValue

```

If it helps, I'm using a wireless keyboard.  But, I've used it before this reformat running ubuntu; never gave me a headache like this.

So it's now affecting emacs.  I wonder if it has something to do w/ X. I was messing around w/ some font smoothing things.

---

### Post by montooner on 2009-03-15
Problem solved; fresh restart =D

---

