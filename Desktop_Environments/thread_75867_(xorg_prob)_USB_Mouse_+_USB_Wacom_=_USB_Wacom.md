---
title: "(xorg prob?) USB Mouse + USB Wacom = USB Wacom"
date: 2005-10-14
forum: Desktop Environments
---

### Post by jasper_m on 2005-10-14
I've attached my /etc/X11/xorg.conf ad xorg.txt to this post. 

Ok, I have USB Mouse and an USB tablet (Wacom Graphire3) connected to my box (Breezy, fresh install from CD). After installation the mouse didn't work really well. It works as long as I'm movin it, but when I leave it alone for a while, it simply stops responding. This can be fixed by switching to one of the terminal screens (Ctrl+Alt+F1) and back to X, but the mouse works only for a while this way... Wacom always works with no problem though.  Worked perfectly with hoary.
     I changed the InputDevice section in xorg.conf to use /dev/input/mouse0 instead of /dev/input/mice. Worked perfectly. Wacom stops working of course. Then I added the inputdevice sections for wacom stuff and added them to the serverlayout. The same problem came again. I've also tried different USB ports for the mouse and the tablet. No effect. Only using mouse0 without InputDevices in ServerLayout works, but that means that the tablet won't.
      Thank you in advance.

  EDIT: Is this the right forum to post this? should it be HW help?

---

### Post by jasper_m on 2005-10-14
I found a serial mouse, no problem anymore... at least for me.

---

