---
title: "Cannot get back into gnome"
date: 2005-05-09
forum: Desktop Environments
---

### Post by deception on 2005-05-09
I set up xcompmgr to load at position "39" as the wiki said to load it before gnome-panel which was set at 40. It seems I did something wrong as now gnome crashes when loading "Window Manager" on start, freezes, and the HD becomes inactive. 

Can anyone tell me the file to edit to get this back to normal please?

Many thanks,
Matt

---

### Post by codejunkie on 2005-05-09
you could try a gnome fail safe session and save those settings on exit if that dosent work restart and choose safe mode under grub list and start x as root and remove the changes you made to  /etc/X11/xorg.conf and reboot.

---

### Post by deception on 2005-05-09
Thanks for your reply! Before you posted I had the idea of uninstalling xcompmgr, getting into gnome, and then setting it to 40. Worked a charm!

Thanks very much for the help,
Matt

---

