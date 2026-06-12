---
title: "Input signal out of range"
date: 2007-11-03
forum: Desktop Environments
---

### Post by luciantodoran on 2007-11-03
When I enter and leave Ubuntu I see an unclear double-image desktop (the image is split in two) with the waiting filling bar with the message: ”Input signal out of range”. I have installed Ubuntu twice and I get the same message. What can I do to solve this problem?:confused:

---

### Post by taurus on 2007-11-03
Can you get to another console with <Ctrl><Alt>F2.  If you can log in from there, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
When you are done with it, press <Alt>F7 to get back to the GUI login screen.  Now, restart X again with <Ctrl><Alt>Backspace.  Does it work now?

---

### Post by luciantodoran on 2007-11-09
Thank you very much; it worked till I had to choose between 16 and 24 at something related to the display. I chose 24 and a black line opened at the bottom saying: ”xerver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf 20071109200500”

Lucian

---

