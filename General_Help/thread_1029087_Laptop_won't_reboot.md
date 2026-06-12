---
title: "Laptop won't reboot"
date: 2009-01-03
forum: General Help
---

### Post by raccoonone on 2009-01-03
I just installed Ubuntu 8.10 on my Presario 3000 Compaq laptop, and it's working pretty well. However restarting it does not work. If I use Restart from the menu, or type "sudo reboot" the computer shutsdown but then stops when the orange bar has become completely black (right before it should poweroff and restart). However, if I do Shutdown from the menu or "sudo shutdown -h now" it will poweroff properly.

Any suggestions as to how I can fix this?

---

### Post by raccoonone on 2009-01-03
I solved the problem. Add "acpi=off apm=power_off" to /boot/grub/menu.lst, under defoptions. and add "apm power_off=1" to /etc/modules

---

