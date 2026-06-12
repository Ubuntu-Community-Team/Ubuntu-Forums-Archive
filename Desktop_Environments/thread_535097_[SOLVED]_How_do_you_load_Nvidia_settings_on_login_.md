---
title: "[SOLVED] How do you load Nvidia settings on login in KDE?"
date: 2007-08-26
forum: Desktop Environments
---

### Post by FuturePilot on 2007-08-26
I have my digital vibrance set to 1 and I would like to have that load when I login to KDE. I know in Gnome you just add nvidia-settings --load-config-only to the System>Preferences>Sessions. But how do you do this in KDE?

---

### Post by quux on 2007-08-26
Put the command you want to execute at KDE login in an executable script in "~/.kde/Autostart/". For a more detailed description see e.g. [http://gentoo-wiki.com/HOWTO_Autostart_Programs#KDE](http://gentoo-wiki.com/HOWTO_Autostart_Programs#KDE)

---

### Post by FuturePilot on 2007-08-26
Thanks! Worked perfectly.:D

---

