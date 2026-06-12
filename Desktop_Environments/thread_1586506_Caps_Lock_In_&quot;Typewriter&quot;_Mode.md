---
title: "Caps Lock In &quot;Typewriter&quot; Mode"
date: 2010-10-02
forum: Desktop Environments
---

### Post by MiSt77 on 2010-10-02
As a first-time poster I would like to start by saying 'Thank you!' - this forum has already saved me much time in the past.

I've used Ubuntu for quite some time now, however, one thing still bugs me: I would like for caps lock to behave like a manual typewriter, i.e. to turn off caps lock, you have to press Shift.

That is, no matter how often I press Caps, it should stay in uppercase mode, only to revert to lowercase after I press Shift:

aaaa <Caps> AAAA <Caps> AAAA <Shift> aaaa

Interestingly, I found a solution for the venerable loadkeys:

[INDENT]```
The  following  entry  sets the Shift and Caps Lock keys to behave more nicely, like in older typewriters. That is, pressing Caps Lock key once or  more sets the keyboard in CapsLock state and pressing either of the Shift keys releases it.

              keycode  42 = Uncaps_Shift
              keycode  54 = Uncaps_Shift
              keycode  58 = Caps_On
```[/INDENT]

Of course I have also looked at setxkbmap and /usr/share/X11/xkb/rules/xorg.lst, but none of the available options seems to cut it, e.g.

[INDENT]```
caps:internal  CapsLock uses internal capitalization. Shift "pauses" CapsLock
```[/INDENT]

is not exactly what I want, since a second Caps key press still switches back to lowercase ...

Any suggestions on how to solve this in X11?

Thank you!

---

