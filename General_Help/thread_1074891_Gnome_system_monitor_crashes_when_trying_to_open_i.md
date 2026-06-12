---
title: "Gnome system monitor crashes when trying to open it"
date: 2009-02-19
forum: General Help
---

### Post by Mercury_Alpha on 2009-02-19
When opening the monitor from the Gnome menu, I get the "Starting System Monitor" tab on the bottom Gnome panel, then it disappears. Starting gnome-system-monitor from a terminal spits out this error:

```
** (gnome-system-monitor:14860): WARNING **: SELinux was found but is not enabled.

terminate called after throwing an instance of 'Gio::Error'
Aborted

```

If I invoke sudo, the terminal comes up right away. I still get the SELinux error, but no "Gio" error.

Google wasn't much help.

---

### Post by Mercury_Alpha on 2009-02-19
Well, I restarted my computer, and that seemed to fix it. Still, I'd like to know what caused it in the first place, because rebooting isn't that great of a workaround.

I had to reboot because Ctrl+Alt+Backspace sent me to a blank screen. The gdm would not load. And Ctrl+Alt+F1 would not bring me a console. But after rebooting, I can restart X without any issues.

:confused:

---

