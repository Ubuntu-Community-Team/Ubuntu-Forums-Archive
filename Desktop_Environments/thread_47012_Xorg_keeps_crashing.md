---
title: "Xorg keeps crashing"
date: 2005-07-06
forum: Desktop Environments
---

### Post by adamb10 on 2005-07-06
Wiether I leave to do something I come back to see Xorg crashed which hangs the system.  It also happens when playing a game.  I do have the Nvidia Drivers installed.

Xorg Log:

[http://adamb10.com/Xorg.0.log](http://adamb10.com/Xorg.0.log)

Xorg.conf:

[http://adamb10.com/xorg.conf](http://adamb10.com/xorg.conf)

Video card is Geforce FX 5200 Ultra

Thanx.

---

### Post by ACK!! on 2005-07-06
[QUOTE=adamb10]Wiether I leave to do something I come back to see Xorg crashed which hangs the system.  It also happens when playing a game.  I do have the Nvidia Drivers installed.

Xorg Log:

[http://adamb10.com/Xorg.0.log](http://adamb10.com/Xorg.0.log)

Xorg.conf:

[http://adamb10.com/xorg.conf](http://adamb10.com/xorg.conf)

Video card is Geforce FX 5200 Ultra

Thanx.[/QUOTE]

Loading a lot of modules.  Try removing from the README on the nvidia site:

Load "dri"
Load "GLcore"

I know, yes I know you do not have GLcore in your config but it also says remove dri and I see you have glx which is good.

Hope that makes a difference but its the only obvious issue I see in the modules section for the Xorg.conf.

---

### Post by frodon on 2005-07-07
I was a bit different for me but ... maybe it will intesrrest you. I've got the same problem, i left my computer 30min and when I came back it was always in login screen. So I solve the problem ..... the **screensaver**  needed to be disable in my case ! Exactly, I've got this problem because it seems than the screensaver was in conflict with xcompmgr (I know you don't use it) but try to disable screensaver and see if your xserver crash again.

---

