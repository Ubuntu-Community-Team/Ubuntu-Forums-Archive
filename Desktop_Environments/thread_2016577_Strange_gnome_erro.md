---
title: "Strange gnome erro"
date: 2012-07-04
forum: Desktop Environments
---

### Post by Tetrohedron on 2012-07-04
I shut down my computer a  few minutes ago and it failed to shut down properly (it closed all applications and then just sat there continuing to shut down).  I impatiently shut my computer down via a hard boot (holding the power button down).  When I restarted my computer to log back in to Ubuntu I could not click on the actions button in the top left corner of gnome or the turn off etc button on the top right corner of gnome.  I hard booted and logged in to repair mode to see if I could perform some sort of system restore.  I could find no way to do it so I selected continue to boot normally.

Anyways, everything works now but my gnome looks different.  Rather than saying "actions" in the top left it says applications.  Rather than my time appearing in center of the bar at the top of the screen it appears in the right.  What happened to my gnome environment and how do I fix it?

---

### Post by kansasnoob on 2012-07-04
It sounds like you may have been using gnome-shell. Is that correct?

If so how did you install gnome-shell?

---

### Post by lolpenguin on 2012-07-05
It may be that you were using GNOME Shell before, but since the hard reboot, something has gone wrong and you have ended up in the fallback session.
Try running ```
gnome-shell --replace
``` and see what happens. Also check your session when you log in.

---

