---
title: "boottext and resolution"
date: 2005-04-07
forum: Desktop Environments
---

### Post by jasplund on 2005-04-07
Is it possible to change the resolution that is used during boot? Cause when I boot now the text looks very big and terribly bad since it's using a very low resolution. When I turn off the computer it's using my regular resolution though. Which it didn't in warty

---

### Post by donar73 on 2005-04-07
- sudo gedit /boot/grub/menu.lst

- for a resolution of 1024x768 @ 16 Bit add vga=0x317 at the end of the line which is responsible for booting your kernel

- save it and reboot

---

### Post by jasplund on 2005-04-07
thanks /J

---

