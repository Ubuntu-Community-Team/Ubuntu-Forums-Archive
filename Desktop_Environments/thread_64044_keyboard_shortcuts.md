---
title: "keyboard shortcuts"
date: 2005-09-09
forum: Desktop Environments
---

### Post by iimess on 2005-09-09
1) What's meta, super, and hyper? Are they just modifiers?

2) I'm trying to add the logo key as modifier, so I tried "Hyper is mapped to Win-keys"
Doesn't seem to work very well. I can assign for example "<mod4>+Home" to show desktop but the same shortcut doesn't work for lock screen or home folder...?

Weird thing is I think I got it work at the very beginning when I ssh'ed to my laptop and changed the keyboard shortcuts with a desktop 105 keyboard, even before I changed the Alt-Win layout options... not sure when and where I messed up.

----------------------------------
FYI:
Toshiba Satellite laptop
Keyboard model uses Generic 105; tried Toshiba S3000
Tried all other Alt-Win options
Removing previously defined mod4 shortcut requires a logout

xmodmap output (Hyper):
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):
                                                                                                                                                             
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Hyper_L (0x73),  Hyper_R (0x74),  Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

Thanks in advance!

---

