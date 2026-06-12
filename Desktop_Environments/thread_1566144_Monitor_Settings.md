---
title: "Monitor Settings"
date: 2010-09-02
forum: Desktop Environments
---

### Post by josmcc on 2010-09-02
Where are the settings stored for monitor resolution in 10.04
I dont' have xorg.conf and can't find anything in /usr/lib/X11/xorg.conf.d or /lib/udev


Found it in ~/.config/monitors.xml

---

### Post by clrg on 2010-09-02
xorg.conf doesn't exist anymore per default. If you need one, simply create it. Put your screen's resolution in there.

---

