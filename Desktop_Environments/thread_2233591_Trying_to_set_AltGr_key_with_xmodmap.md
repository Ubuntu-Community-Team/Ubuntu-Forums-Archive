---
title: "Trying to set AltGr key with xmodmap"
date: 2014-07-09
forum: Desktop Environments
---

### Post by LonelyStar on 2014-07-09
Hey,

I use a us-intl with "AltGr dead keys" layout and the option to switch Alt and Win key. Nice, but my AltGr does not work. The key I want to use for AltGr has keycode 134 (found out using xev). So I create a .Xmodmap file:

```

keycode 134 = ISO_Level3_Shift Multi_key ISO_Level3_Shift Multi_key

```

than I execute "xmodmap .Xmodmap". When I now show my modifier, I get:

```

> xmodmap
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock      
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x85),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x40),  Super_R (0x6c),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  ISO_Level3_Shift (0x86),  Mode_switch (0xcb)

```

But ... pressing "AltGr" (the key with code 134=0x86) + "q" does not give the expected result - which would be "a-umlaut".
It should! xmodmap -pke contains this line:

```

keycode  24 = q Q q Q adiaeresis Adiaeresis adiaeresi

```

So what is wrong and what can I do?

Thanks!
Nathan

---

