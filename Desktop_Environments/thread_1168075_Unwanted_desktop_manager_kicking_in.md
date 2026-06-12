---
title: "Unwanted desktop manager kicking in"
date: 2009-05-23
forum: Desktop Environments
---

### Post by desperateone on 2009-05-23
Every time I log in, the XFCE loading screen goes up, loading things, xfdesktop among them. But at some time during the loading, the desktop becomes plain brown, the icons change, icons for media devices appear, clearly another desktop manager is kicking in (the GNOME one, based on some error messages). Now I've been ignoring it, running xfdesktop covers it up, but it was too much when it started happening on my other computer. Running a tiling window manager, xmonad. Anyone has any idea how to stop this?

---

### Post by Locutus_of_Borg on 2009-05-23
what is in your autostart directory/file?

something is probably loading nautilus, which unless you run it nautilus --no-desktop, will load the gnome desktop as well

---

### Post by desperateone on 2009-05-24
> **Locutus_of_Borg said:**
> what is in your autostart directory/file?

I'm not sure what you mean, but if you mean the .xinitrc, I don't have one, so I guess things are loaded from some default file.

> **Locutus_of_Borg said:**
> something is probably loading nautilus, which unless you run it nautilus --no-desktop, will load the gnome desktop as well

Well, on one of the computers it might make sense, because it's actually Ubuntu with XFCE, but the other one is pure Xubuntu, and I don't have Nautilus there.

---

