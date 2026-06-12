---
title: "&lt;Ctrl&gt; key misbehaving with desktop effects"
date: 2009-04-07
forum: General Help
---

### Post by twent4 on 2009-04-07
Hey guys,
Just switched to Gnome from KDE, everything is working real nice unless i turn on desktop effects and become unable to use the most basic keyboard shortcuts. The ctrl key pretty much kills any input from the keyboard when pressed, so any combinations of keys hit after the keypress go unnoticed. heres the output of **xev | grep key**, which were just me trying to hit <Ctrl>A

```
anton@kdesk:~$ xev | grep key
    keys:  4294967173 0   0   0   16  0   0   0   0   0   0   0   0   0   0   0
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
    keys:  4294967237 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
    keys:  4294967190 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
    keys:  4294967190 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

is this a compiz/metacity issue...? is that what gnome even uses for compositing?

thanks

---

