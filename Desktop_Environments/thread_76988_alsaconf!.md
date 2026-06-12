---
title: "alsaconf?!"
date: 2005-10-16
forum: Desktop Environments
---

### Post by unexpected on 2005-10-16
Does anyone know why alsaconf isn't included in the Ubuntu repositories?

Does anyone know where i can download this utility?

---

### Post by Riverside on 2005-10-16
[QUOTE=unexpected]Does anyone know why alsaconf isn't included in the Ubuntu repositories?

Does anyone know where i can download this utility?[/QUOTE]For whatever reason, the Ubuntu developers have apparently made a decision so ship a crippled version of the ALSA system, with alsaconf removed.  Both of my desktop machines have onboard Intel sound chips, and getting sound working with all other distributions is simplicity itself; post installation, run alsaconf as root and sound is configured and working within seconds.  In contrast, I have only ever succeeded in getting sound working in Ubuntu 4.10, and never since (sound "just worked" in 4.10, but I wasn't able to get sound working at all in 5.04 despite having spent hours Googling and searching these forums and trying the various methods/workaround suggested therein).

My guess is that the only way to get sound working in Ubuntu versions more recent than 4.10 on this system would be to uninstall ALSA post installation, then download the ALSA source code and build and install it from source, then run alsaconf.  I haven't yet tried doing that though, although as I am now installing 5.10 I may give it a go.

---

### Post by Riverside on 2005-10-16
[QUOTE=Riverside]My guess is that the only way to get sound working in Ubuntu versions more recent than 4.10 on this system would be to uninstall ALSA post installation, then download the ALSA source code and build and install it from source, then run alsaconf.  I haven't yet tried doing that though, although as I am now installing 5.10 I may give it a go.[/QUOTE]No need in fact; sound "just works" in 5.10, as it did in 4.10.  alsaconf is a highly useful tool though, and can get sound working and configured on extremely otherwise recalcitrant systems in my experience.  A shame that the Ubuntu developers see fit to reduce the ALSA functionality by removing it.

---

### Post by aham925925 on 2005-10-17
[QUOTE=Riverside]No need in fact; sound "just works" in 5.10, as it did in 4.10.  alsaconf is a highly useful tool though, and can get sound working and configured on extremely otherwise recalcitrant systems in my experience.  A shame that the Ubuntu developers see fit to reduce the ALSA functionality by removing it.[/QUOTE]
Sound doesn't just work for me in Breezy..Are you saying if i Download ALSA like you said befor and build it then sound will work?

---

