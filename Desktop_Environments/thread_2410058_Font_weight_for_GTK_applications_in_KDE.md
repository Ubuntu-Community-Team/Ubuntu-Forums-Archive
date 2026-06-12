---
title: "Font weight for GTK applications in KDE"
date: 2019-01-10
forum: Desktop Environments
---

### Post by CatKiller on 2019-01-10
After I installed Kubuntu 18.04 I was using the Ubuntu font in KDE and for GTK applications, and it all worked OK. I've since switched to Source Sans Pro, which works great for native things, but isn't getting picked up properly by GTK applications. Firefox and Thunderbird are the ones I use.

As far as I've been able to check, it picks up the right font family but not the weight. I want it to use the Regular weight, the same as everything else, but it's choosing the Light weight instead. The Ubuntu font doesn't have a Light weight, which I think is why that didn't happen before. The Light weight for Source Sans Pro is first in the list in the font chooser of System Settings, which is probably significant: it picks the first match it finds from the right family and calls it a day.

Has anyone else seen this, and managed to fix it?

---

### Post by CatKiller on 2019-01-10
OK, so I removed all the other fonts so that **only** Regular weight was available. The GTK fonts are still coming up lighter.

I suspect that GTK is simply terrible at handling fonts.

[ATTACH=CONFIG]282168[/ATTACH]

---

