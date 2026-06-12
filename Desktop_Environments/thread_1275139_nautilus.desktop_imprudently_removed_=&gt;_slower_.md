---
title: "nautilus.desktop imprudently removed =&gt; slower bootstrap?"
date: 2009-09-25
forum: Desktop Environments
---

### Post by lompa on 2009-09-25
Hi, while performing some system cleanup I imprudently deleted my "nautilus.desktop" file. Of course I made a new one, I managed to have it aotoload on login, but since then my laptop boots more slowly (more in detail: I get a black screen for 10-20 secs after log in). There must be something wrong with the new file I made, or the load sequence has somehow changed... here's how my new nautilus.desktop file loos like:

```
lompa@dida112:~$ more /usr/share/applications/nautilus.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Nautilus File Manager
Comment=Start nautilus file manager
TryExec=nautilus
Exec=nautilus
Icon=system-file-manager
Terminal=false
StartupNotify=false
Type=Application
NoDisplay=true
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Autostart-enabled=true
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus
```

Can you post how your file looks like? Thanks a lot in advance!

Lompa

---

