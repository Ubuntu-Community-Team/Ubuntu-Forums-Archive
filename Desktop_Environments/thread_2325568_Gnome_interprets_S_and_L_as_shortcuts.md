---
title: "Gnome interprets S and L as shortcuts"
date: 2016-05-23
forum: Desktop Environments
---

### Post by dwigyit on 2016-05-23
Seemingly at random, my GNOME 3.20 environment on Ubuntu Gnome 16.04 has started interpreting every unshifted L as a shortcut to Gnome Help and every S as a toggle for the on-screen keyboard. The backspace key also does not work, but doesn't seem to trigger anything. This makes typing essentially impossible. Using an external keyboard does not help, but the problem does not occur in KDE.

I checked my custom shortcuts in Gnome Keyboard Settings and there was nothing unusual. There also seemed to be no similar shortcuts, so I'm confident it's not just a case of a meta key misbehaving on my laptop keyboard (although I have also checked that numlock etc are not turned on). Has anyone experienced anything similar or have any ideas for how to investigate?

---

### Post by CantankRus on 2016-05-24
Check how keys behave using **onboard** (onscreen keyboard).

---

### Post by dwigyit on 2016-05-24
Interesting. I installed onboard and it has exactly the same issues (S and L do the wrong things). Gnome 3's built in keyboard is slightly different. It turns itself off with the S key as expected but does type the L key as it should (without opening help).

---

### Post by skewty2 on 2016-08-10
I had the same issue; you aren't going crazy :)

I couldn't figure it out, gave up and re-formatted the partition and went with Ubuntu Gnome instead.  A few gnome-shell extensions and I'm happy.  I couldn't stand the 1 pixel gap between the Unity Launcher and any maximized window's left side (it's there by design, not a bug, and to me unacceptable).
Now if only I could rotate my displays using mutter.  :)

---

