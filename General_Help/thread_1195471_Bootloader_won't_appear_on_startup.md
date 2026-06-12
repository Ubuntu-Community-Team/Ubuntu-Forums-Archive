---
title: "Bootloader won't appear on startup"
date: 2009-06-23
forum: General Help
---

### Post by jrcraft on 2009-06-23
Installed Xubuntu 9.04 via Wubi on old Dell Inspiron 8200 yesterday.

Computer restarted after turning on restricted Nvidia drivers, factory splash screen gone, OS selection won't show up. Wait a minute and Windows starts up normal.

I rebooted the machine and hit the down arrow, then enter. Xubuntu starts but still no image on screen. Hit ctrl-alt-f1 to get in via tty1. Edited xorg.conf to point to laptop display for X server. Rebooted machine, Dell splash and bootloader still won't show up. Down arrow + enter to select Xubuntu, GUI started and displayed normally at full resolution.

How do I get my factory splash and bootloader back? Did something get changed in the BIOS somehow or is it a GRUB issue?

---

### Post by zvacet on 2009-06-24
Press Esc and you should be able to see grub.Maybe it is somehow hidden and you can change that if you edit menu list

```
gksudo gedit /boot/grub/menu.lst
```

find lines

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

and if last line is without # sign add it in front of line.Save and close file.Reboot and now you should see grub.

---

