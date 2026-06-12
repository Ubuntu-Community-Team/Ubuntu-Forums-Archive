---
title: "cannot save chnages Xconfiguration file."
date: 2009-11-06
forum: Desktop Environments
---

### Post by meeya on 2009-11-06
I'm using 9.10 64 bit. when I change the CRT resolution to a different one than the default I cannot save the changes to the xconfiguration file, it says failed to pass existing x config file '/etc/X11/xorg.conf'

---

### Post by Kushkah on 2009-11-06
Do you have an nvidia graphics card? If so, you just need to remove your old xorg.conf file and let nvidia-settings generate it's own.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will make a backup of your xorg.conf file and make a backup.  Also, try running nvidia-settings as root:
```
gksu nvidia-settings
```
And you should be able to save a new configuration file.

---

### Post by meeya on 2009-11-06
thanks buddy it worked!

---

