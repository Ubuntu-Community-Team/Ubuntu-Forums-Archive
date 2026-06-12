---
title: "Need address for panel launcher"
date: 2012-09-06
forum: Desktop Environments
---

### Post by holadebob on 2012-09-06
Can someone tell me the command to use to enable a launcher to open up a samba network folder? The folder that I want a launcher to open is listed under Places/Network in the nautilus file manager that I'm using.

Xubuntu 12.04

---

### Post by LewisTM on 2012-09-06
The command is
[FONT="Courier New"]gvfs-open smb://server/share[/FONT]
Cheers!

---

### Post by holadebob on 2012-09-07
Thank you!

---

### Post by LewisTM on 2012-09-07
No problem.
To be more precise, [FONT="Courier New"]gvfs-open[/FONT] will open a Samba share that is already connected. [FONT="Courier New"]gvfs-mount[/FONT] will connect and mount it so you might need to run it first e.g. at login.

A shortcut would be to use [FONT="Courier New"]exo-open <address>[/FONT] or simply[FONT="Courier New"] thunar <address>[/FONT]. Both commands will mount the share and open the file manager.

---

