---
title: "Logitech keyboard - xev returns &quot;button &lt;number&gt;&quot; instead of keycode"
date: 2008-04-09
forum: Desktop Environments
---

### Post by EvolutionByMemes on 2008-04-09
I'm having a little trouble nailing down my keyboard configuration. I'm using Hardy, and most of my media keys on my logitech cordless access keyboard work by default (YAY). The problem arises with the alternate F-Keys (there is an F-lock modifier key to switch between normal f1 - f12 and alternate functions including some media keys and other shortcut keys). I followed the instructions I found on google for mapping the keys using xmodmap to assign the keycode from xev to a specific function, but xev returns "button 81" - "button 92" rather than a keycode. I get the same results using evdev as the keyboard driver as I do using the default kbd driver.

Here is my output from xev when I click mouse button 1 (works and returns button), then "x" (works and returns keycode), and then "My Music" (which does not work, and returns button 92).

```

ConfigureNotify event, serial 31, synthetic NO, window 0xe00001,
    event 0xe00001, window 0xe00001, (783,74), width 178, height 178,
    border_width 2, above 0x2a00007, override NO

ButtonPress event, serial 31, synthetic NO, window 0xe00001,
    root 0x1a6, subw 0x0, time 2135530, (129,6), root:(914,82),
    state 0x10, button 1, same_screen YES

ConfigureNotify event, serial 31, synthetic YES, window 0xe00001,
    event 0xe00001, window 0xe00001, (783,74), width 178, height 178,
    border_width 2, above 0x2400a7c, override NO

ButtonRelease event, serial 31, synthetic NO, window 0xe00001,
    root 0x1a6, subw 0x0, time 2135546, (129,6), root:(914,82),
    state 0x110, button 1, same_screen YES

KeyPress event, serial 31, synthetic NO, window 0xe00001,
    root 0x1a6, subw 0x0, time 2138440, (129,6), root:(914,82),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XmbLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0xe00001,
    root 0x1a6, subw 0x0, time 2138528, (129,6), root:(914,82),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

ButtonPress event, serial 31, synthetic NO, window 0xe00001,
    root 0x1a6, subw 0x0, time 2140289, (129,6), root:(914,82),
    state 0x10, button 92, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0xe00001,
    root 0x1a6, subw 0x0, time 2140385, (129,6), root:(914,82),
    state 0x10, button 92, same_screen YES

```

I searched all over for any posts regarding this issue and couldn't find any. I thought it would be a good opportunity to make my first post. :)
If anyone has this same issue, or preferably a solution to it, it would be greatly appreciated.

---

