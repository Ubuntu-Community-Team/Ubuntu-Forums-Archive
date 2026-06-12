---
title: "Screen Resolution"
date: 2009-04-09
forum: General Help
---

### Post by ultblad1 on 2009-04-09
After installing some updates, my computer's screen resolution is at a maximum of 800 by 600. Before it was at a standard 1280 by 1024, without any special drivers.

The monitor is an old CRT, and before it did not complain when I plugged it in and set the screen resolution higher. I'm not completely sure why the screen resolution dropped.

Does anyone have any ideas why this happened?

---

### Post by Claus7 on 2009-04-09
Hello,

it is common problem after an update the graphics card not to work properly. Can you see at /etc/X11/ directory any backup of your xorg.conf file that it might work or if you can manually configure the xorg.conf file?

Also I would try the command gksudo nvidia-settings.

Regards!

---

### Post by ultblad1 on 2009-04-10
Thanks for the help, but it turns out that all I needed to do was to restart the computer. I'm not sure why Ubuntu did not recognize my monitor the first time..

---

