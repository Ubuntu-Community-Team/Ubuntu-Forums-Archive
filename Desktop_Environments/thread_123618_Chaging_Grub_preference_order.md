---
title: "Chaging Grub preference order"
date: 2006-01-30
forum: Desktop Environments
---

### Post by bmccruz on 2006-01-30
How can i change the Grub preference order so it boots first windows and not linux

---

### Post by art on 2006-01-30
change in the /boot/grub/menu.lst the line where it sais 'default 0' to whichever you want

---

### Post by bmccruz on 2006-01-30
i got the grub installed on the partition of windows can i also that command  even so?

---

### Post by mcduck on 2006-01-30
Or set it to 'saved' to boot the last selected OS.

And yes, GRUB options are still stored on your Linux partition, and you can change them with 'sudo gedit /boot/grub/menu.lst'.

---

### Post by bmccruz on 2006-01-30
k thantks alot

---

