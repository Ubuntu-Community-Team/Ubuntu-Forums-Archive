---
title: "screen is offset to the right and looks like hell"
date: 2006-04-22
forum: Desktop Environments
---

### Post by mister lahey on 2006-04-22
I have tried different refresh rates and resolutions but the display is offset and flickery on 2 different monitors. I think it did something to the video card, when I boot from 'doze it's still messed up. I was going to toss this monitor out, but I tried it on another machine and it's fine. The card is an Nvidia 440Mx. It worked perfectly before installing Umbuntu.

---

### Post by dreamsINdigital on 2006-04-22
Adjust your monitor with the buttons on it.  It probably has an auto-adjust feature too...

---

### Post by mister lahey on 2006-04-22
I installed the nvidia glx driver and it corrected the offset problem. It's still flickery but it is a pos crt monitor that needs to be smashed with a bat. ;)

---

### Post by Jason_25 on 2006-04-22
You might be running it at 60 hz.  Chances are it will do at least 75 hz.  Edit the  /etc/X11/xorg.conf file to fix this.  The gnome screen resolution utility might do it too.

---

