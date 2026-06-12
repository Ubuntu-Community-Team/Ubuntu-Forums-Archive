---
title: "Is it possible to remap key to ISO_Level3_Shift?"
date: 2009-06-16
forum: General Help
---

### Post by kubaz on 2009-06-16
Hello,

I am trying to create two keys that should serve as the same modifier key. On is AltGr, which is standardly mapped to ISO_Level3_Shift. But when I call

```
xmodmap -e "keycode 64 = ISO_Level3_Shift"
```which, I supposed, should map also left alt to ISO_Level3_Shift, both keys start to behave incorrectly. In some programs, they do exactly what I expect. In others, however, they (in combination with other keys) send different characters than they are supposed to - for example, in terminal I see only question marks instead of the expected symbols. Is it a bug?

---

### Post by sdennie on 2009-06-16
It's possible that left alt is still mapped to the mod1 modifier so it's sending both alt and ISO_Level3_Shift (or something crazy like that).  What is the output of "xmodmap"?

---

### Post by kubaz on 2009-06-17
Oh, thanks, I am stupid :). After assigning  ISO_Level3_Shift to the left alt key, it also became a "trigger" for mod1:

```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        ISO_Level3_Shift (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

I don't know whether this is a correct behaviour... Nevertheless, the command xmodmap -e "clear mod1" did the trick.

---

