---
title: "MAME screen not centered"
date: 2011-08-02
forum: Gaming &amp; Leisure
---

### Post by Luke M on 2011-08-02
Trying to get MAME v0.141 to work...one problem is that the screen is not centered (in the default full screen mode). It's shifted far to the right so only half the emulated screen is visible. Performance is another issue - not sure what options to use to get decent speed.

---

### Post by Luke M on 2011-08-03
More info: the centering works when the screen is not rotated. It is apparently centering as if 1920x1080 rather than 1080x1920. I think the extremely bad performance is caused by DirectFB not working (so falling back to ultra slow X11 mode), but I don't know why it's not working. Another issue - if I allow MAME to change video modes, it doesn't change back after exit, so I have to logout to get back to normal.

---

