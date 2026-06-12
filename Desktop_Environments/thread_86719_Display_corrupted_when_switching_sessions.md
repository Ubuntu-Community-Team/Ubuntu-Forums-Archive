---
title: "Display corrupted when switching sessions"
date: 2005-11-06
forum: Desktop Environments
---

### Post by dmh-bidlah on 2005-11-06
When I start a new X session (KMenu->Switch User->Start New Session) then the appearing display is corrupted, like sliced into pieces or something. I recently did an upgrade to KDE 3.5 Beta 2, but the problem was already present in KDE 3.4.3.
Thanks for any help.

---

### Post by mlomker on 2005-11-06
I've heard the same complaint from gnome users.  It must be a problem with the video driver that you are using...unless X is broken, which is entirely possible given all of the modularization changes that occured in Breezy.

---

### Post by dmh-bidlah on 2005-11-06
I also recently switched drivers, from "ati" to "fglrx" to get 3D acceleration. I will see what it does when I change the drivers back.

---

### Post by dmh-bidlah on 2005-11-07
When I switched back to "ati" i could start a new X session but I didn't have 3D acceleration, so no Enemy Territory or other 3D games for me. I switched back to fglrx for now. Is it possible to configure fglrx so it can create a new screen?
Thanks...

---

### Post by mlomker on 2005-11-07
> Is it possible to configure fglrx so it can create a new screen?


No, it's a [known issue]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.18.8.html#178361") even in the latest driver.

---

### Post by dmh-bidlah on 2005-11-07
Well, I've currently switched back to "ati". But I've heard sometinh about a "radeon" driver, does that work in Ubuntu? I cannot choose it when i configure xserver-xorg.

---

