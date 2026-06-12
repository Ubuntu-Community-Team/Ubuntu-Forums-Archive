---
title: "how to change screen resolution using the terminal?"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by bosshoof on 2007-05-25
[B]i installed the KDE on xubuntu
but i can't change the screen resolution

so please , tell me
How to change screen resolution using the terminal?
to say : 1024*768
[/B]

---

### Post by disgustingangel on 2007-05-25
try using the command xrandr
without parameters it gives you the supported resolutions, and you can set the resolution using:

xrandr -s <resolution index from the resolutions list>
or
xrandr -s <x_res>*<y_res>

if you need more informations take a look at 
man xrandr

---

