---
title: "Problem with multimedia keys"
date: 2012-08-30
forum: Desktop Environments
---

### Post by xternal7 on 2012-08-30
I have a laptop, and multimedia keys (next song, previous song) used to work with Amarok. I also have an external keyboard which I sometimes use (mostly as remote for switching songs from my bed). But the keyboard doesn't have the next/previous song keys, so I googled thing up and modded the key actions with xev and Xmodmap. (Two extra keys for next song, two extra keys for previous song).

And it worked. In fact, it worked a bit too well. **THE PROBLEM IS,** Amarok (and Minirok, too) &#8212; which are pretty much the only two audio playing programs supporting global shortcuts &#8212; now use only one key, on my external keyboard, for next and one from previous song. Only one for each action. Worst part is that now the previous/next track keys on my laptop keyboard **do not work at all**. So, any ideas on how get all keys to work?






Extra details:
xev detects all three keys I've mapped for "next track" as "next track" key, output is identical to the original prev/next track key (with exception of keycode), same goes for all three 'previous song" keys. Settings in all programs detect all three "next song" keys as "next song" key, but Amarok and Minirok will execute the correct action only when one of the three is pressed. (Same goes for "previous song" keys)
[B]
xev says this:[/B]
[I]
"Next Song" keys:[/I]
(Laptop internal keyboard, not working):
```

KeyPress event, serial 32, synthetic NO, window 0x5a00001,
    root 0xa9, subw 0x0, time 20867615, (1076,596), root:(1080,614),
    state 0x10, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XKeysymToKeycode returns keycode: 163
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x5a00001,
    root 0xa9, subw 0x0, time 20867622, (1076,596), root:(1080,614),
    state 0x10, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XKeysymToKeycode returns keycode: 163
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```


(External keyboard key that executes the action assigned):
```
FocusOut event, serial 35, synthetic NO, window 0x5a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 35, synthetic NO, window 0x5a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  4294967295 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   8   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 35, synthetic NO, window 0x5a00001,
    root 0xa9, subw 0x0, time 21098896, (1133,744), root:(1137,762),
    state 0x10, keycode 163 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

(External keyboard key that doesn't work):
```
KeyPress event, serial 35, synthetic NO, window 0x5a00001,
    root 0xa9, subw 0x0, time 21326657, (1087,691), root:(1091,709),
    state 0x10, keycode 167 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XKeysymToKeycode returns keycode: 163
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x5a00001,
    root 0xa9, subw 0x0, time 21326876, (1087,691), root:(1091,709),
    state 0x10, keycode 167 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XKeysymToKeycode returns keycode: 163
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Same patterns appear at 'previous song' keys.

Xmodmap contents:
```
keycode 171 = XF86AudioNext
keycode 173 = XF86AudioPrev
keycode 167 = XF86AudioNext
keycode 163 = XF86AudioNext
keycode 180 = XF86AudioPrev	
keycode 166 = XF86AudioPrev
```

---

