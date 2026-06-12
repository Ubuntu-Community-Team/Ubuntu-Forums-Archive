---
title: "Switch framebuffer output to external display"
date: 2014-05-10
forum: Desktop Environments
---

### Post by Bill_Carson on 2014-05-10
Hello everyone,

Whenever I use my laptop at my desk, I usually connect it to an external display on DP-1.
To switch the window manager output to this display, I can just use "**xrandr --output DP-1 ...**"
However, whenever I switch to another virtual tty (e.g. because I messed up again and X is frozen),
the output is only shown on the laptop display (LVDS-1).  This is quite annoying if the laptop lid is closed
(because when I open it again there are acpid events that lock the screen, etc.).

_*My question*:_ is there an "**xrandr**" equivalent for tty framebuffers?
By this I mean: is there an easy way to switch the output from the framebuffer to the external monitor?

I've searched this question on google, but all I seem to find is people suggesting me to use **vbetool**,
of which I have no idea how to use.
Any advice would be greatly appreciated! :)

---

