---
title: "usplash / console resolution - not displaying"
date: 2006-06-08
forum: Desktop Environments
---

### Post by mikeym on 2006-06-08
Hi, 

My usplash and console ([alt]+[ctrl]+F1 etc. ) are not displaying properly on my flat screen monitor and nvidia graphics card - TNT2 running legasy drivers. It appears to crop about a third of the screen. 

Does anyone know how I can fix this?

I changed my /etc/X11/xorg.conf to only include the modes available in my monitors manual, but I wasn't sure how to change the horizontal and vertical refresh rates as they are listed for my monitor as 31.469-79.976 Horiz and 59.94-75.029 with different values for each of the modes.

---

### Post by fmo on 2006-06-08
to change te graphic mode of your console, you need to modify the parameters passed to your kernel in the file "/boot/grub/menu.lst", you need to locate the vga=xxx related to your kernel (usually the first on the list) and modify it to a screen resolution supported by your screen.

If you are not sure of what mode to use, you can try "vga=normal" but you splashscreen will disapear.

---

