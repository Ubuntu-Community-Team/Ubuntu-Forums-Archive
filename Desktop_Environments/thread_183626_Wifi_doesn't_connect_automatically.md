---
title: "Wifi doesn't connect automatically"
date: 2006-05-28
forum: Desktop Environments
---

### Post by sambram on 2006-05-28
Hey all. My issue isn't a hardware problem, wifi works. However, my configuration does not load straight from boot. As in, syncing to ntp doesn't work and once KDE has started I have to go into KWifiManager/KCMWifi and hit "activate" to connect to my WLAN. I have "load preset configuration on startup" checked. 

This is not a big problem, but a decent annoyance. I'd be greatful if there's an easy solution here. :)

**[Edit:** I just realized I put this in the wrong forum. I'm sorry!**]**

---

### Post by tkjacobsen on 2006-05-28
try adding "auto wlan0" to /etc/network/interfaces. (if wlan0 is you wireless device): To edit interfaces open a terminal and type:
```
sudo nano /etc/network/interfaces
```

---

### Post by sambram on 2006-05-28
Hmm, It appears to already be there, actually.

---

### Post by vidak on 2006-05-29
i'm not sure about this,but... is there another network card? Maybe it should be disabled by default

---

