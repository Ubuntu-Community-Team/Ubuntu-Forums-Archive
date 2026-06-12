---
title: "How to get Alt_R to behave as Alt and ISO_Level3_Shift"
date: 2010-05-25
forum: Desktop Environments
---

### Post by mandar.mitra on 2010-05-25
I'm using Ubuntu 10.04. When I use the Gnome desktop, the right alt behaves perfectly (alt ordinarily, but as ISO_Level3_Shift when I switch keyboard layout). When I use fvwm (as I do usually), it is always mapped to ISO_Level3_Shift and it stops behaving as the Alt key.


Is there some way that I can get the Gnome behaviour under Fvwm as well?


Thanks.

---

### Post by simosx on 2010-05-27
> **mandar.mitra said:**
> I'm using Ubuntu 10.04. When I use the Gnome desktop, the right alt behaves perfectly (alt ordinarily, but as ISO_Level3_Shift when I switch keyboard layout). When I use fvwm (as I do usually), it is always mapped to ISO_Level3_Shift and it stops behaving as the Alt key.


Is there some way that I can get the Gnome behaviour under Fvwm as well?

In GNOME run
[INDENT]
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/INDENT]
in order to capture the precise keyboard settings that work.
From the result you get, use 'setxkbmap' to replicate those settings in fvwm.

---

### Post by mandar.mitra on 2010-07-06
Thanks for your reply. It turns out I had provided wrong information in my original post, but I eventually managed to get things to work the way I wanted.


I looked at "xmodmap -pke" and put the following in my .Xmodmap:


```
keycode 108 = Alt_R Meta_R ISO_Level3_Shift
```


This makes things work the way I like.

---

### Post by simosx on 2010-07-06
Several keyboard layouts include an instruction that converts the AltGr into ISO_Level3_Shift.
Most probably your second layout is such a layout.
The xmodpad rule you use simply disables the functionality to use AltGr on that second layout to type extended Unicode characters.

---

