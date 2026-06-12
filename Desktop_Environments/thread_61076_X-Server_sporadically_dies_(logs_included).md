---
title: "X-Server sporadically dies (logs included)"
date: 2005-08-30
forum: Desktop Environments
---

### Post by aquaboot on 2005-08-30
Hi,

I've just installed ubuntu 5.04 on two different desktops using gnome 2.10.  After an hour or so with my screensavers on (default screensavers that came with the os) my x server quits and I get thrown back to a command line with the following debugging info:




Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

Any ideas on what's going on?

Thanks much,

aquaboot

---

### Post by skoal on 2005-08-30
logs included? Those debooger statements you gave above are just warnings, and not causing your problem.  I think what's happening here is your screensaver _eventually_ gets around to an OpenGL one (since by default it's set to display random ones).

sol'n: pick just one SS (not random), or resolve any GL problems associated with your video driver.

...that's my best guess.

\\//_

---

