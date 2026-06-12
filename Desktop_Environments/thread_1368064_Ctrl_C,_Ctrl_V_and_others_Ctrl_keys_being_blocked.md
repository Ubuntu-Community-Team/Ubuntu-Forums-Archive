---
title: "Ctrl C, Ctrl V and others Ctrl keys being blocked"
date: 2009-12-30
forum: Desktop Environments
---

### Post by JohnEv on 2009-12-30
Certain Ctrl key combinations e.g. C,V and F are being blocked, others are not. The output from running  keymap -i input/eventX shows a response from the keys Ctrl C and V separately but no response when used as a combination:-
keycode 54 = (keysym 0x63, c), state = 0x10           #C key 
keycode 37 = (keysym 0xffe3, Control_L), state = 0x10 #Ctrl key pressed
     c key pressed here but no response!
keycode 37 = (keysym 0xffe3, Control_L), state = 0x14 #Ctrl key released

The PC is based upon an Asus PV4V533-MX motherboard with a standard 102 keyboard.  A clean install of Ubuntu 9.10. was done yesterday. I have not any problem before with Ubuntu 7.10 up to 9.04. 

Copy/cut and paste operation have to be done using the right mouse button in all programs where applicable. 

Any suggestions gratefully received

---

### Post by archeryguru2000 on 2010-03-24
JohnEv, have you found a solution to this problem?  I too am having the exact same problem(s).  I began with a fresh install of Karmic on my work computer late last week, and have yet to resolve this issue.

Let me know if you've found a solution.

~~archery~~

---

### Post by super.openid on 2011-11-21
I'm having the same trouble, except only Ctrl+v is not working.  Running xev gives the following:
```
$ xev
KeyPress event, serial 30, synthetic NO, window 0x3c00001,
    root 0x79, subw 0x0, time 262194288, (997,844), root:(1001,892),
    state 0x10, keycode 55 (keysym 0x76, v), same_screen YES,
    XLookupString gives 1 bytes: (76) "v"
    XmbLookupString gives 1 bytes: (76) "v"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3c00001,
    root 0x79, subw 0x0, time 262194368, (997,844), root:(1001,892),
    state 0x10, keycode 55 (keysym 0x76, v), same_screen YES,
    XLookupString gives 1 bytes: (76) "v"
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x3c00001,
    root 0x79, subw 0x0, time 262196424, (997,844), root:(1001,892),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 33, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  0   0   0   0   32  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 33, synthetic NO, window 0x3c00001,
    root 0x79, subw 0x0, time 262198840, (997,844), root:(1001,892),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

^C
$
```i.e., when I press Ctrl+v, FocusOut and FocusIn events are recorded, and then a KeymapNotify hijacks my "v".

Everything was working fine until I tried to fix the problem with F11 and F12 being mapped to middle-click and right-click (PPC defaults I think).  I was able to get F11 and F12 working properly, but somehow it broke Ctrl+v.

I never mapped the v key, and I don't even know how to remap a combination of keys.  So, I'm at a loss as how to reverse my changes.

---

