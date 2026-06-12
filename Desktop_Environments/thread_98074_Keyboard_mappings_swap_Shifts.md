---
title: "Keyboard mappings: swap Shifts"
date: 2005-12-02
forum: Desktop Environments
---

### Post by Cyhatch on 2005-12-02
Problem:

Got three keyboard layouts: [FONT="Courier New"]en[/FONT], [FONT="Courier New"]lt[/FONT] and [FONT="Courier New"]ru[/FONT]. The Group Shift/Lock behavior is set to "Alt+Shift changes group".

I want to use Alt + Left Shift for layout switching.

When in [FONT="Courier New"]en[/FONT], either [FONT="Courier New"]Alt[/FONT] + [FONT="Courier New"]Shift_L[/FONT] does nothing, while either [FONT="Courier New"]Alt[/FONT] + [FONT="Courier New"]Shift_R[/FONT] changes to the next layout. When in the [FONT="Courier New"]lt[/FONT] or [FONT="Courier New"]ru[/FONT] layouts, [FONT="Courier New"]Alt[/FONT] + [FONT="Courier New"]Shift_R[/FONT] changes to the next layout while [FONT="Courier New"]Alt[/FONT] + [FONT="Courier New"]Shift_L[/FONT] changes to the previous.

[FONT="Courier New"]xmodmap[/FONT] output:

```
shift       Shift_L (0x32),  Shift_R (0x3e)
```

So, I decided to swap the shifts: ran this through [FONT="Courier New"]xmodmap[/FONT]:

```
remove Shift = Shift_L
remove Shift = Shift_R

keysym Shift_L = Shift_R
keysym Shift_R = Shift_L

add Shift = Shift_L
add Shift = Shift_R
```

[FONT="Courier New"]xmodmap[/FONT] output:

```
shift       Shift_L (0x3e),  Shift_R (0x32)
```

Now I can't use the Shifts for layout switching at all. They do work though.

---

### Post by Cyhatch on 2005-12-03
Okay, drop this one. Using the winkey.

---

