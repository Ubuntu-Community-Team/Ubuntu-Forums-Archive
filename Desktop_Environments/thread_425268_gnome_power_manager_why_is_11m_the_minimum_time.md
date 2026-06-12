---
title: "gnome power manager: why is 11m the minimum time?"
date: 2007-04-27
forum: Desktop Environments
---

### Post by schmolch on 2007-04-27
Is this some weird joke or something, its starting to annoy me.

---

### Post by schmolch on 2007-04-27
ok i have read on the mailinglist why that is.

gnome-power-manager sets the minimum time to the time of gnome-screensaver +1.
gnome-screensaver's default time is 10m, so gnome-power-manager adds 1 because to avoid beeing started before the screensaver.

So if you want less then 11m you can set the gnome-screensaver to 1m, then the minimum time for gnome-power-manager will be 2m.

They should just ignore the screensaver, who cares about a stupid screensaver anyways?

---

