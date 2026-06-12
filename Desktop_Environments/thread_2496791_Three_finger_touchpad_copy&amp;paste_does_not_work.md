---
title: "Three finger touchpad copy&amp;paste does not work (Ubuntu 22.04)"
date: 2024-04-12
forum: Desktop Environments
---

### Post by danjde on 2024-04-12
Hi Friends,
I've just upgraded from Ubuntu 20.04 to Ubuntu 22.04, and I'm using GNOME Shell 42.9.
On Ubuntu 20.04 I was able to highlight text and then paste it with three fingers using the touchpad.

Now on Ubuntu 22.04 and GNOME Shell 42.9 this is no longer possible, even if enabled on Gnome Tweak Tool > Mouse&Touchpad: "emulate three fingers for middle click".

I'm using Wayland
```
echo $XDG_SESSION_TYPE
wayland
```

The curious thing is that I can copy & paste with Libreoffice or firefox but not between native gnome applications (gedit, terminal or others)


Iìve try to run as root:

```
 libinput debug-events
```

the three fingers touch does not show any output, all other gestures give correct output.

What else could I do?


Many thanks!

---

### Post by danjde on 2024-05-01
HI.
Should I open up to askubuntu?

---

