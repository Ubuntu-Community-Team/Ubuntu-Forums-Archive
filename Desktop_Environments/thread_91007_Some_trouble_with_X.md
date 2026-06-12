---
title: "Some trouble with X"
date: 2005-11-16
forum: Desktop Environments
---

### Post by vootele on 2005-11-16
When I want to start a new X session (from menu or from "Swich user" button with locked screen, something goes wrong and it says "there were errors starting X server"
When I log in, it says 6 times that the maximum limit of the flexible X servers reached.
i thin I added debian sarge repository for a while and did some updates from there...could this be the cause?

---

### Post by zAo on 2005-11-16
[QUOTE=vootele]When I want to start a new X session (from menu or from "Swich user" button with locked screen, something goes wrong and it says "there were errors starting X server"
When I log in, it says 6 times that the maximum limit of the flexible X servers reached.
i thin I added debian sarge repository for a while and did some updates from there...could this be the cause?[/QUOTE]
The problem will be that Sarge repro. Sarge uses XFree86, while Breezy uses Xorg.

---

### Post by vootele on 2005-11-16
sarge is removed for some time now. Should I just wait for next X update?

---

