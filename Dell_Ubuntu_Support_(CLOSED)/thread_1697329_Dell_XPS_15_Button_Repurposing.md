---
title: "Dell XPS 15 Button Repurposing"
date: 2011-02-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lagonium on 2011-02-28
Hey everyone, I have a question about changing what the three touch-sensitive buttons do on my XPS 15 L501x.  I've checked for the keycodes with xev, but I really don't know what to do with them.  

I want to make one of the three buttons open the Terminal, another open Thunderbird, and I haven't decided what I want the third one for.  How do I set keybindings in a simple and reliable way?

This is the output I recorded with xev for each of the three keys:
```

[SIZE=3]Settings button (brings up mobility center in windows)[/SIZE]

KeyPress event, serial 33, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 2159750, (-318,-120), root:(867,443),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 2159752, (-318,-120), root:(867,443),
    state 0x40, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XmbLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 2159756, (-318,-120), root:(867,443),
    state 0x40, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 2159762, (-318,-120), root:(867,443),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

[SIZE=2]
[SIZE=3]Three-prong thing (brings up quick-launcher in windows)[/SIZE][/SIZE]

FocusOut event, serial 36, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  
[SIZE=3]
[/SIZE][SIZE=3]MaxxAudio button (brings up Waves MaxxAudio center in windows)[/SIZE]

FocusOut event, serial 36, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

```

---

### Post by mskrzypczak on 2011-06-01
I definitely agree with a question. Does anyone has any idea?

---

### Post by Cmorais on 2011-07-25
I got the same question. I could remap using xev, showkeycode and setkeycode.

I used the xev and showkeys to get the map for the key, then I set a arbritary not used yet key, as "cancel" or "redo" and assign in keyboards shortcuts.

The problem that I didn't care about is that all setkeycode should be done by super user. I think you'll need to do some RC stuff to apply it properly.

---

