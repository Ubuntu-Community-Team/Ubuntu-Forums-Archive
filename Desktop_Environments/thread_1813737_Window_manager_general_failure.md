---
title: "Window manager general failure"
date: 2011-07-28
forum: Desktop Environments
---

### Post by gradysghost on 2011-07-28
I installed Xubuntu 11.04 a few days ago, and everything's been more or less fine since then.  But I installed some updates last night, paying no attention to what they were, and this morning I logged in to find problems.

Open windows do not get registered with window listings (like in the top panel, for instance).  All windows open above desktop panels, and cannot be moved behind them.  Some windows open with their title bars above the top frame of the screen, but Alt + Click/Drag doesn't grab the window.  Maximizing and minimizing windows do not work.  There is simply no reaction to clicking them.  I logged out and also restarted the system to see if it was a fluke, but it's not.

Otherwise, everything still seems to be functional.  I'm writing this post from the laptop that's having the problem.  I'm going to try uninstalling the crappy ATI video drivers and see if that resolves the problem, but any help from the interwebz would be greatly appreciated.  Sounds like an X problem to me, if I had to guess, but I'm not sure if 11.04 has X or Wayland or what.

---

### Post by gradysghost on 2011-07-28
UPDATE!

After noticing that there were actually no window decorations whatsoever, I ran:

```
xfwm4 --replace
```

That has resolved the problem.  For now.

I'm about to restart to unload the video card driver, and I'll post the results here when I'm done.  The point is that I'm now asking the question Why isn't xfwm launching with my desktop?

---

### Post by gradysghost on 2011-07-28
Looks like forcing xfwm to run solved the problem.  I've reinstalled the ATI drivers, and everything is still working.

---

