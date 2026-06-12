---
title: "Invalid keyboard key mapping after installing ubuntu 14.04"
date: 2014-04-20
forum: Desktop Environments
---

### Post by zubin2 on 2014-04-20
Upon installing Ubuntu 14.04, I find that the back/forward special keys on my kinesis keyboard no longer work (they used to work fine with ubuntu 10.04).  Further investigation with xev showed that the correct keypress events are not being sent in this version of ubuntu.  When the "back" key is pressed, we get the following sequence of events:
[LIST=1]
[*]KeyPress for Alt_L
[*]KeyRelease for Alt_L
[*]KeyRelease for Left
[/LIST]
The expected sequence should have been:
[LIST=1]
[*]KeyPress for Alt_L
[*]KeyPress for Left
[*]KeyRelease for Alt_L
[*]KeyRelease for Left
[/LIST]
which would have correctly simulated pressing Alt-Left on the keyboard.

This is the stock install (I've not modified any key mappings using xmodmap or any other program).

Would appreciate any help tracking down why there is a missing keypress event, and suggestions for how to fix it.  Below is the output from xev.
Thanks!

[FONT=courier new]When "Back" key on keyboard is pressed:[/FONT]
[FONT=courier new]=======================================[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyPress event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 120081, (56,178), root:(1751,230),[/FONT]
[FONT=courier new]    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XmbLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]FocusOut event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    mode NotifyGrab, detail NotifyAncestor[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]FocusIn event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    mode NotifyUngrab, detail NotifyAncestor[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeymapNotify event, serial 37, synthetic NO, window 0x0,[/FONT]
[FONT=courier new]    keys:  2   0   0   0   0   0   0   0   1   0   0   0   0   0   2   0   [/FONT]
[FONT=courier new]           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   [/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyRelease event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 120169, (56,178), root:(1751,230),[/FONT]
[FONT=courier new]    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyRelease event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 120169, (56,178), root:(1751,230),[/FONT]
[FONT=courier new]    state 0x0, keycode 113 (keysym 0xff51, Left), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]When "Alt+Left" is pressed:[/FONT]
[FONT=courier new]===========================[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyPress event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 314505, (106,177), root:(1801,229),[/FONT]
[FONT=courier new]    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XmbLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]FocusOut event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    mode NotifyGrab, detail NotifyAncestor[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]FocusOut event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    mode NotifyUngrab, detail NotifyPointer[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]FocusIn event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    mode NotifyUngrab, detail NotifyAncestor[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeymapNotify event, serial 37, synthetic NO, window 0x0,[/FONT]
[FONT=courier new]    keys:  2   0   0   0   0   0   0   0   1   0   0   0   0   0   2   0   [/FONT]
[FONT=courier new]           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   [/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyPress event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 314601, (106,177), root:(1801,229),[/FONT]
[FONT=courier new]    state 0x8, keycode 113 (keysym 0xff51, Left), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XmbLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyRelease event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 314633, (106,177), root:(1801,229),[/FONT]
[FONT=courier new]    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]KeyRelease event, serial 37, synthetic NO, window 0x3600001,[/FONT]
[FONT=courier new]    root 0x2bc, subw 0x0, time 314673, (106,177), root:(1801,229),[/FONT]
[FONT=courier new]    state 0x0, keycode 113 (keysym 0xff51, Left), same_screen YES,[/FONT]
[FONT=courier new]    XLookupString gives 0 bytes: [/FONT]
[FONT=courier new]    XFilterEvent returns: False[/FONT]

---

