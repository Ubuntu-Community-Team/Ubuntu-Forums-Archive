---
title: "Right Alt-key, Alt-Gr, not working with desktop effects"
date: 2010-10-10
forum: Desktop Environments
---

### Post by Sithun on 2010-10-10
"Normal" and "Extra" desktop-effects makes the right alt-key break. Making such daily activities such as programming or writing an email nigh impossible, or at least very difficult, since the symbols @, £, $, €, ¥, {, [, ], } and \ simply cannot be written. Disabling desktop effects solves the problem, and re-enabling them doesn't make the problem appear anew. until i reboot, then its there again.

This should probably be in the "100 paper-cuts" for Ubuntu, or whatever its called, but since I seem to be the only one being able to produce this error on the entire interwebs, that would seem somewhat unnecessary. And before you slam me with any clever quips about using the forums search-function, ill just say that I found lots of alt-key related problems, but no problem like mine. :)

Thanks for any help. Ill give you any information you think is related to my problem.

---

### Post by Sithun on 2010-10-20
Oh for the love god, nobody experiences this? Should i be concerned that the error is with my bloody *keyboard*?

---

### Post by P4man on 2010-10-20
Run "xev' in a terminal and see what happens when you press that key with the effects on and off. I can only think you configured some shortcut key in a compiz plugin?

---

### Post by Sithun on 2010-10-24
Ofcourse. :)

On pressing AltGR (right alt-key), while using unmodified compiz-settings for "Extra Desktop Effects" [COLOR="DarkRed"](This is when AltGr doesn't work.)[/COLOR]:
> FocusOut event, serial 33, synthetic NO, window 0x4e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x4e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


After switching to "Visual effects: None" and back again to "Visual effects: Extra" [COLOR="Blue"](Now, AltGr works again.)[/COLOR]:
> KeyPress event, serial 36, synthetic NO, window 0x5800001,
    root 0xd5, subw 0x0, time 88413891, (1859,415), root:(1862,463),
    state 0x10, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x5800001,
    root 0xd5, subw 0x0, time 88414542, (1859,415), root:(1862,463),
    state 0x90, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


Also, excuse the smilies in the last quote, I didn't figure out how to get rid of them

---

### Post by P4man on 2010-10-24
So, its definitely a compiz plugin setting, since it doesnt work with compiz settings, but it works with "desktop effects" set to extra ( which also uses compiz, just no plugins).

I would just rename the ~/.compiz/ folder to  ~/.compiz-backup/ or something and see if that cures it. Then reconfigure your compiz plugins as you like.

If I misunderstood or am wrong, you could also check in system > preferences > keyboard > layout > options and see if you configured something for altgr.

BTW, to get rid of the smileys, use **code** tags
```
:)
```
Not **quote** tags
> :)

---

### Post by mcduck on 2010-10-24
> **P4man said:**
> So, its definitely a compiz plugin setting, since it doesnt work with compiz settings, but it works with "desktop effects" set to extra ( which also uses compiz, just no plugins).


Actually that would mean the problem was in some of the Compiz settings Sithun has set himself in Compiz options. Probaly he simply had accidentally set the keyboard shortcut for something to use the AltGr key. 

The "Normal" and "Extra" settings for Compiz (in Appearance preferences) use Compiz and it's plugins just like any custom settings would. They are simply pre-configured setups with certain plugins enabled and certain configuration options set. That's why the setting changes to "Custom" immediately when you change something in CompizConfig Settings Manager, if you change the settings you are not using any of the presets any more. ;)

---

### Post by Sithun on 2010-12-28
> **mcduck said:**
> Actually that would mean the problem was in some of the Compiz settings Sithun has set himself in Compiz options. Probaly he simply had accidentally set the keyboard shortcut for something to use the AltGr key. 

The "Normal" and "Extra" settings for Compiz (in Appearance preferences) use Compiz and it's plugins just like any custom settings would. They are simply pre-configured setups with certain plugins enabled and certain configuration options set. That's why the setting changes to "Custom" immediately when you change something in CompizConfig Settings Manager, if you change the settings you are not using any of the presets any more. ;)

This ofcourse solves the long-lasting problem i had.
The problem consisted of compiz loading its custom-settings when ubuntu started, but not loading them when I switched from "no desktop effects" to "Extra desktop effects", thus not occupying the alt-gr button anymore.

I have no idea what compiz-plugin that casued the problem, i.e. had alt-gr bound to some command, but i'm fairly certain that I never bound that button to anything (is it a standard setting for some plugin?).

I solved this by resetting compiz to its standard settings, then added plugins as I see fit (grid and wobbly windows).

Thanks for the help and sorry for being a tosser. :)

---

