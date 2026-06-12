---
title: "Unity Graphical Glitch"
date: 2011-04-29
forum: Desktop Environments
---

### Post by mpace965 on 2011-04-29
So after I upgraded to 11.04 I was messing around in Compiz to tweak some things back. Doing so resulted in Unity crashing. So I logged out and logged back in, but now when I use the application switcher, these black lines appear on the top bar. Also the dock and top bar are black until the window comes completely into view. See screenshots for details.

#1 Pertains to the black lines
#2 Pertains to the black dock

Any suggestions?

---

### Post by mpace965 on 2011-04-30
Bump?

---

### Post by MugOTea on 2011-04-30
Can you remember what you changed in Compiz Config Manager. I'm no expert but I did the same thing while enabling special effects and just fiddled until it went away - I might remember what I did if you can recall what you changed before the problem started.

For some reason Unity (top bar) seems to crash readily when ccm is used or updated. Usually a logout an back in will recover it?

---

### Post by mpace965 on 2011-04-30
Thanks for the response. I have tried logging out and back in and restarting. The main thing is I enabled wobble windows and messed around with the application switcher. I also started up Gnome and did a reinstall of Unity from Synaptic. Although I only marked Unity and none of the other packages so I'll mark Unity and all related packages for reinstallation.

---

### Post by mpace965 on 2011-04-30
Okay I think I got it. I was using the Shift Switcher, so instead now I'm on the Ring Switcher. I also ran
```
gconftool-2 --recursive-unset /apps/compiz-1
```
and then
```
unity --reset
```

---

