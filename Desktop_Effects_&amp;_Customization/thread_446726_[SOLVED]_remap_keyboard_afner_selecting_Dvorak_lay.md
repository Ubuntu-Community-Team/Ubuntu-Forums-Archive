---
title: "[SOLVED] remap keyboard afner selecting Dvorak layout"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by raequin on 2007-05-17
Wten I was using the QWERTY layout I was able to remap the right win key to "Control_R."  Now that I switched to the Dvorak layout, the same command,


xmodmap -e "keycode 116 = Control_R"


doesn't work.  There is a difference in the output of xev between the two layouts.  QWERTY gives


KeyPress event, serial 26, synthetic NO, window 0x2a00001,
    root 0x3e, subw 0x2a00002, time 2587715518, (40,33), root:(45,105),
    state 0x2, keycode 116 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2a00001,
    root 0x3e, subw 0x2a00002, time 2587715526, (40,33), root:(45,105),
    state 0x42, keycode 116 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes:


, while Dvorak gives


KeyPress event, serial 26, synthetic NO, window 0x2a00001,
    root 0x3e, subw 0x2a00002, time 2587078103, (53,34), root:(58,106),
    state 0x0, keycode 116 (keysym 0xffe4, Control_R), same_screen YES,
    XKeysymToKeycode returns keycode: 109
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2a00001,
    root 0x3e, subw 0x2a00002, time 2587078243, (53,34), root:(58,106),
    state 0x0, keycode 116 (keysym 0xffe4, Control_R), same_screen YES,
    XKeysymToKeycode returns keycode: 109
    XLookupString gives 0 bytes:


So it seems that the difference is the line


    XKeysymToKeycode returns keycode: 109.


Can anybody tell me how to remap this key with the Dvorak layout and what the XKeysymToKeycode is doing here?

---

