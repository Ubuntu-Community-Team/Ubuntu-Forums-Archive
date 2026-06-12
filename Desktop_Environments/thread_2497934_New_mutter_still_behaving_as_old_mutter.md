---
title: "New mutter still behaving as old mutter"
date: 2024-05-23
forum: Desktop Environments
---

### Post by kozimodo2 on 2024-05-23
I dist-upgraded from mantic to noble and the new mutter has the same [problem]("https://gitlab.gnome.org/GNOME/mutter/-/issues/2954") as the old mutter.  The problem doesn't exist with a fresh noble install.  Is there some gconf setting that can fix this?

---

### Post by ActionParsnip on 2024-05-24
Possibly a setting in
```

$HOME/.config

```
Somewhere. I'm guessing there is a mutter config file you can rename then log off and on to get vanilla settings, then reconfigure

---

### Post by kozimodo2 on 2024-05-24
If there's a mutter config file, it's well hidden:
> $ ls .config/
autostart/  libreoffice/    simple-scan/  gedit/
GIMP/                     micro/          tiling-assistant/     glib-2.0/
monitors.xml    transmission/    gnome-initial-setup-done  Code/
gnome-session/            nautilus/       ubuntu-xdg-terminals.list       GNOME-xdg-terminals.list
pdfarranger/    update-notifier/    dconf/      goa-1.0/
user-dirs.dirs   enchant/    gtk-2.0/                  pulse/
user-dirs.locale    eog/        gtk-3.0/                  xdg-terminals.list
evince/     gtk-4.0/                  QtProject.conf    evolution/
ibus/ 

---

### Post by ActionParsnip on 2024-05-24
> **kozimodo2 said:**
> If there's a mutter config file, it's well hidden:

OK... Then maybe look online to see where it is hidden....

---

