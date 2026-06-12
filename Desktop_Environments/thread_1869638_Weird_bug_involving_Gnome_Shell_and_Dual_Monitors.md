---
title: "Weird bug involving Gnome Shell and Dual Monitors"
date: 2011-10-26
forum: Desktop Environments
---

### Post by FatalChaos on 2011-10-26
I have a laptop with an nvidia video card (560m, tested with both drivers offered) I use with a monitor, with the monitor above the laptop. On Unity, everything runs as expected. On Gnome Shell though, I cannot drag windows from my laptop monitor to my other monitor. However, if I change the setup in nvidia settings so that the monitor is not oriented directly above the laptop monitor, I can drag windows from one monitor to the other. It does appear though that unless my monitor is directly to the side of the laptop monitor that there are invisible barriers to where I can drag windows. Any thoughts on what is going on?

---

### Post by Vorik_ on 2012-01-08
I've got the same issue, have you found a way to fix it perhaps?

Thanks,
Ger.

---

### Post by FatalChaos on 2012-01-15
> **Vorik_ said:**
> I've got the same issue, have you found a way to fix it perhaps?

Thanks,
Ger.

I did not find a solution other than to change the orientation of the two monitors to something that did not reflect the physical layout.

I think the problem is that the way Twinview works is that it combines your two monitors into one giant virtual monitor. However, for whatever reason the supported virtual monitor size is limited, and when your virtual monitor exceeds it nvidia or xorg shits the bed without giving you a nice warning.

---

