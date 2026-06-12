---
title: "kde draws dialog window frames too big"
date: 2007-11-05
forum: Desktop Environments
---

### Post by AlmaTlust on 2007-11-05
KDE draws dialog windows too big - I always have to scroll down and left to click a button (e.g. within a system settings sub dialog, but also some other dialog windows). I tried changing the monitor settings (even manually in xorg.conf with providing screen measurements), but that doesn't help.
The problem exists in both Feisty and Gutsy. Changing font size doesn't help either, because there's lots of empty space in drop down menus and stuff.
Any hints how to change this?

---

### Post by mexlinux on 2007-11-05
I'm not sure I got your problem, could you post a screenshot? (for better understanding)

---

### Post by TeaSwigger on 2007-11-05
> **AlmaTlust said:**
> KDE draws dialog windows too big - I always have to scroll down and left to click a button (e.g. within a system settings sub dialog, but also some other dialog windows). I tried changing the monitor settings (even manually in xorg.conf with providing screen measurements), but that doesn't help.
The problem exists in both Feisty and Gutsy. Changing font size doesn't help either, because there's lots of empty space in drop down menus and stuff.
Any hints how to change this?

Guess I'll have to second the request for screenshots. I've never had such a problem in my Kubuntu. Only dialog windows? Did you specify any "special application settings"? If you specify say 800x600 under application settings, it'll also open other windows parented by that app at that size.

---

### Post by AlmaTlust on 2007-11-06
as you can see on the screenshot, there's plenty of space on the right side and the bottom, but still I have to scroll down to reach the apply button (my system is German, so I don't know how all the stuff is called in English - sorry)

---

### Post by bailout on 2007-11-06
I seem to remember this was 'solved' for system settings a few releases ago and came back with the next release. It is really annoying and is just poor design. Often, as in your screenshot, there doesn't seem any rason for the 'window' to need to use scrolls but even when it is needed the buttons should always be visible.

---

### Post by AlmaTlust on 2007-11-07
is there a way to manually tweak this? Or would that mean to recompile KDE?

---

