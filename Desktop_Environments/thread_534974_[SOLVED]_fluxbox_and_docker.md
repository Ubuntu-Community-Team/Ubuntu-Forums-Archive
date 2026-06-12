---
title: "[SOLVED] fluxbox and docker"
date: 2007-08-25
forum: Desktop Environments
---

### Post by quantumcheese on 2007-08-25
I just started using the docker app with my fluxbox wm to put gnome dockapps into my slit.

I run several gnome daemons; in particular, gnome-power-manager, which I configured to display only while the battery is in use (no AC or recharging).  However, when the battery finishes charging and the docked icon disappears, the icon next to it begins to oscillate between its position and the recently vacated position.

Anyone have suggestions how to make the empty spot go away?

---

### Post by quantumcheese on 2007-08-26
It's actually worse than this -- gnome-power-manager now causes my other applets to move back and forth at login, until I kill it.  It's quite annoying for the visual reason and because it means I can't have the power manager running...

---

### Post by kerry_s on 2007-08-26
i don't fully understand.

sudo apt-get install scrot
scrot 1.jpg

please post the pic here using the "manage attachements" below.
will look like this->

---

### Post by quantumcheese on 2007-08-26
So I took these screencaptures; they're a few seconds apart because I had bad timing, but it illustrates the point -- about every half-second, the spot gnome-power-manager doesn't occupy either does or does not exist; compare the lower-right corner, and now imagine that these two screenshots alternate every 0.5 second
.

---

### Post by kerry_s on 2007-08-26
hmm, interesting never seen that before. what happens if you put it to always show whether it is charging or not? other wise i would say it was a bug with docker not being able to coup with the icon appearing & disappearing, kinda like not refreshing properly.

---

### Post by quantumcheese on 2007-08-26
When I set it always to display, then the icon is constant.  Therefore, I believe that this is a docker refresh bug.  How can I file this?
Thanks.

---

### Post by quantumcheese on 2007-12-09
This is not a problem in Gutsy.

---

