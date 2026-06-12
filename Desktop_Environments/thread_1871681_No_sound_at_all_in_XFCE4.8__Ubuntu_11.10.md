---
title: "No sound at all in XFCE4.8 / Ubuntu 11.10"
date: 2011-10-29
forum: Desktop Environments
---

### Post by cl17g on 2011-10-29
I have installed XFCE4.8 to avoid Unity in Unbuntu 11.10. As far as I can see, all applications that work under Unity work fine also under XFCE4.8, EXCEPT all those dealing with sound (Skype included). Do you have any suggestion?

Linux 3.0.0-12
Ubuntu 11.10
XFCE4.8
Asus U5F

---

### Post by Toz on 2011-10-29
Hello and welcome to the forums.

Try adding:
```
options snd-hda-intel model=laptop-eapd 
```
...to the end of **/etc/modprobe.d/alsa-base.conf** and rebooting.

Reference links:
- [http://www.linlap.com/wiki/asus+u5f]("http://www.linlap.com/wiki/asus+u5f")
- [http://ubuntuforums.org/showthread.php?t=1541971&page=4]("http://ubuntuforums.org/showthread.php?t=1541971&page=4")

---

### Post by cl17g on 2011-10-29
Thank you for your answer!

However, after a couples of days struggling on the issue, I found right now that for some reason I could not modify the volume setting that I set in Unity. I re-installed xfce4-mixer and, after some more trials, things are working now. Still, I don't understand why it was not working before.

---

