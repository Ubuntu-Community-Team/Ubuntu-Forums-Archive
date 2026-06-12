---
title: "xfce4-session save/restore fail if gthumb is running"
date: 2011-10-25
forum: Desktop Environments
---

### Post by gmargo on 2011-10-25
New install with xubuntu-desktop, I'm running xfce.

Normally, upon logout, the session is saved and then restored upon login.

However, certain program(s) cause a failure.  I've only seen this with **gthumb** but others may have the same problem.

If gthumb is running, then the log out procedure hangs for a long time (10-15 seconds?).  When I log back in, then the window manager (xfwm4) is **not** started, so all the restored windows dump into location 0x0 without any borders.  (Recovery is possible by removing $HOME/.cache/sessions/*).

Probably this represents a bug in **xfce4-session**, but why?  Is there a bug in **gthumb** too?  Can anyone duplicate this result?

---

