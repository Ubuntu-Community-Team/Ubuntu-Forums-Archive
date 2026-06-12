---
title: "xfce4 problem with hotkeys"
date: 2009-02-28
forum: Desktop Environments
---

### Post by ventolin on 2009-02-28
Hi,

I've remapped my right control key on my keyboard to "XF86AudioNext" by putting the following line in my .xinitrc:

xmodmap -e "keycode 105 = XF86AudioNext"

This works for the other two keys I've remapped (right windows key and the "menu key"). I've verified that this is "working", in essence, by starting xev and pressing the right control button. What I get is:
```

KeyRelease event, serial 34, synthetic NO, window 0x5000001,
    root 0x8b, subw 0x0, time 6813468, (-95,145), root:(656,596),
    state 0x4, keycode 105 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
I can map commands to my right windows key and menu key fine, without problems. However, when I try to use the right control button as a trigger, it doesn't except it (probably because Control_R is originally a modifier - however, i've already changed it to map to XF86AudioNext!)

How do I fix this? Any help would be greatly, greatly appreciated.. thanks

---

