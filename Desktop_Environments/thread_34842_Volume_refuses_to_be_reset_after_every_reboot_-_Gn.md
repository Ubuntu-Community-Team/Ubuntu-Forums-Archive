---
title: "Volume refuses to be reset after every reboot - Gnome"
date: 2005-05-16
forum: Desktop Environments
---

### Post by pirast on 2005-05-16
Hi,
after every reboot the volume is muted. Then I have to open the gnome mixer and make it louder.

After rebooting the volume is muted again.

How to eliminate it?

Martin

---

### Post by Knome_fan on 2005-05-16
Open a terminal:
sudo dpkg-reconfigure alsa-base
choose to always save automatically

That should be it.

---

### Post by pirast on 2005-05-20
[QUOTE=Knome_fan]Open a terminal:
sudo dpkg-reconfigure alsa-base
choose to always save automatically

That should be it.[/QUOTE]
 Thanks but it didn't work. Any other ideas?

Martin

---

