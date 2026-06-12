---
title: "AltGr+Shift not the same as Shift+AltGR"
date: 2006-07-25
forum: Desktop Environments
---

### Post by m83 on 2006-07-25
I using Ubuntu 6.06 and I have this problem that's really annoying. When I press AltGr+Shift (AltGr then Shift) is not the same as when I press Shift+AltGr (Shift then AltGr).

I have configured two layouts: gb (I have a UK keyboard) and ro (as I'm romanian). Changing between the two layouts works fine, no problem here. I can even use AltGr+whatever to obtain the characters that are configured. What I don't manage to obtain is the characters that are configured for using with AltGr+Shift.

Here is what my "InputDevice" section in xorg.conf looks like:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "gb,ro"
        Option          "XkbVariant"  ",std"
        Option          "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
        Option          "AutoRepeat"    "250 30"
EndSection
```

Regardless of the layout that's currently active, when I press AltGr then Right Shift (AltGr+Shift) I get the characters that I get when I press only AltGr (this is incorrect). When I press Right Shift then AltGr (Shift+AltGr) I obtain the characters that are configured for the forth level in the keymap (this is correct).

For example, in the romanian layout, when I press AltGr+[, I obtain [; when I press AltGr+Shift (AltGr then Shift), I obtain the same [, as if I only pressed AltGr (I should have obtained {); when I press Shift+AltGr (Shift then Altgr) I obtain { like it supposed to be.

I have run xev to view what symbols are produced when I press AltGr+Shift and Shift+AltGr. Here is what I found (don't know what to make of it though...):

when I press Shift then AltGr:
```
KeyPress event, serial 26, synthetic NO, window 0x3800001,
    root 0x4c, subw 0x0, time 2776635468, (551,473), root:(561,533),
    state 0x0, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x3800001,
    root 0x4c, subw 0x0, time 2776636395, (551,472), root:(561,532),
    state 0x1, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
```

when I press AltGr then Shift:

```
KeyPress event, serial 29, synthetic NO, window 0x3800001,
    root 0x4c, subw 0x0, time 2776640728, (551,470), root:(561,530),
    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x3800001,
    root 0x4c, subw 0x0, time 2776641687, (551,470), root:(561,530),
    state 0x80, keycode 62 **(keysym 0x0, NoSymbol)**, same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
```

The "keysym 0x0, NoSymbol" part really puzzles me... It should have been ISO_Level3_Shift, like when I press Shift+AltGr, no?

I'm wondering why AltGr+Shift (AltGr then Shift) is not the same thing as Shift+AltGR (Shift then AltGr). This is really annoying.

I found a [bug]("https://bugs.freedesktop.org/show_bug.cgi?id=2871") in the freedesktop.org bugzilla that is quite old: is opened on 2005-03-31. Nobody seems to know the answer... :(

---

### Post by anasofiapaixao on 2006-08-14
I can't reproduce this bug, but try this:
```
sudo xmodmap -e "keycode 50 = Shift_L Shift_L Shift_L Shift_L Shift_L Shift_L"
sudo xmodmap -e "keycode 62 = Shift_R Shift_R Shift_R Shift_R Shift_R Shift_R"
```
I am suggesting this because AltGr is a modifier by itself and maybe for some reason, pressing AltGr then Shift will activate Shift's fifth level keysym; This way you actually have something configured for Shift's fifth level, kind of forcing Shift to be Shift.

Mind you I am not sure at all if this will work, but it musn't hurt to try...

---

