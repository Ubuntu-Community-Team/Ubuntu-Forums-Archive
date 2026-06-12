---
title: "gconf-editor changes not having effect"
date: 2009-01-11
forum: Desktop Environments
---

### Post by Spad on 2009-01-11
I've just rebuilt my laptop with 8.10 and I can't get rid of the desktop icons for mounted volumes.

I've followed the same process I did the last time and made the changes in gconf-editor under apps->nautilus->desktop, but it doesn't seem to make any difference; the icons are still all there.

I've rebooted and gone back into gconf-editor and the settings are "correct", but the icons remain on my desktop.

Any idea where I might be going wrong?

---

### Post by mcduck on 2009-01-11
First, surely you are not starting the gconf editor with sudo or gksudo? As that would mean you'd be editing root's settings, not your own..

Second, you could try restarting Nautilus after making the changes (although they _should_ load immediately). To restart Nautilus open a terminal and run "killall nautilus" (you only need to stop it, it will respawn automatically when killed).

---

### Post by Spad on 2009-01-11
*beats head repeatedly against desk*

Yup, gksudo - force of habit I'm afraid.

All sorted now, thanks :)

---

