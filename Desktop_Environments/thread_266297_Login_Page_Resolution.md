---
title: "Login Page Resolution"
date: 2006-09-27
forum: Desktop Environments
---

### Post by indytim on 2006-09-27
My login page resolution has gone way LARGE (probably 800x600 or larger).  I was adjusting my display resolution on a KDE session just before this occurred.  Don't know if that has a bearing on it or the condition was the result of a recent update.  btw- it's not a driver issue as the video is happy under both KDE and Gnome.

Looking for hints on getting the login page back to the default resolution (I do frequent switching between KDE and Gnome and.... Win2k).

Many Thanks,

IndyTim

---

### Post by Bachstelze on 2006-09-27
```
sudo vim /etc/X11/xorg.conf
```

scroll down to the section where all video modes (depth+resolution) are listed and remove everything but your preferred mode. Then restart X with Ctrl+Alt+BkSp

---

