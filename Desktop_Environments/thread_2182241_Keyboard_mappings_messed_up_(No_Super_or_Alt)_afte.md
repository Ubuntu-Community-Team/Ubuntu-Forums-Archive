---
title: "Keyboard mappings messed up (No Super or Alt) after dist-upgrade to 13.10"
date: 2013-10-20
forum: Desktop Environments
---

### Post by sunbird on 2013-10-20
I recently dist-upgraded to 13.10. There used to be a handy keyboard settings page where you could fix common keyboard mapping problems, but that screen appears to be gone in 13.10, so I'm left to wrestle with xmodmap.

My initial problem is that I have no Alt or Super keys, which makes it impossible to use any keyboard shortcuts. Using the following ~/.xmodmap file, I now get the proper responses on xev for the keys.

```

remove Control = Control_L
remove Control = Alt_L
remove Control = Super_L
remove Control = ISO_Level5_Shift
remove mod1 = Super_L
remove mod1 = Alt_L
remove mod4 = Super_L
keycode 64 = Alt_L
keycode 133 = Super_L

add Control = Control_L
add mod4 = Super_L

```

So when I run xev | grep keycode, I get:

```

    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,

```

Where 133 is the super key and 64 is the Alt key. So far, so good.

The problem is, the system seems to think that super = Alt. E.g. when I type Super+Tab I get the dash search bar. When I press Super_L it shows the dash. According to my keyboard settings control panel, these are mapped to Alt_L. Still no super key.

I do notice some strangness here:

```

$ xmodmap -pm
xmodmap:  up to 2 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        ISO_Level3_Shift (0x86),  Meta_L (0xcd)
mod2        Num_Lock (0x4d),  BadKey (0xcf)
mod3        ISO_Level5_Shift (0xcb)
mod4        Super_L (0x85),  Super_L (0xce)
mod5        ISO_Level3_Shift (0x5c)

```

In that there is a second Super_L and a "BadKey" that seems strange...

Ideas on how to fix this?

---

