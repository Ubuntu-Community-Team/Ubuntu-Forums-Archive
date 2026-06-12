---
title: "Panels loading, unloading in a continuous cycyle"
date: 2010-04-28
forum: Desktop Environments
---

### Post by Frogster on 2010-04-28
Hello everyone,

I have a problem with the top panel in 9.10. It keeps loading/unloading "white squares" and that means the desktop is unusable as I cant get to any icons to try and correct it!

Starting in Gnome failsafe mode and the problem doesn't happen, probably because Compiz isn't loaded

I cant even get to my backups to restore

Any ideas/help will be greatly received, even if it is returning the panel to it default settings

---

### Post by 2hot6ft2 on 2010-04-28
You can reset the panels to their default.
Use Alt+F2
and follow these instructions (**be very careful with the second one**)
> **lidex said:**
> Terminal:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Frogster on 2010-04-29
Thank you lidex,

```
gconftool --recursive-unset  /apps/panel
```

Worked a treat

:)

---

