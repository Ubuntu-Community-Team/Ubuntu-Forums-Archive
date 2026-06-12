---
title: "Reboot or Shutdown from a WDM managed session"
date: 2005-10-21
forum: Desktop Environments
---

### Post by hoodwink on 2005-10-21
I'm running a kubuntu 5.10 (upgraded from 5.04) system, but I don't really use KDE or GNOME. I've installed IceWm as my desktop manager, and I've implemented WDM as my session/login manager. I like unbloated software.:) 

One problem I don't know how to solve in Debian based systems is this: WDM has options for Reboot and Shutdown, but these do not work at present. The only way I can shutdown is XTL-ALT-Fn and use the 3 fingered salute.

Does anyone know how to enable Reboot/Shutdown in WDM or any other non-KDE/GNOME setup?

---

### Post by hoodwink on 2005-10-24
After several days of searching and RTFM, I found the answer. For those who need to know:

in /etc/X11/wdm/wdm-config, you must change the line

DisplayManager*wdmRoot:         true

to

DisplayManager*wdmRoot:         false

Sigh. It's really tooo baaad :( that the setting preferred by the vast majority of users is not the default.

---

