---
title: "trouble switching to stumpWM"
date: 2013-01-11
forum: Desktop Environments
---

### Post by korgoth28 on 2013-01-11
I decided to try a tiling window manager. Since I like emacs and lisp, I chose stumpWM. I installed the package, moved the existing files in /usr/share/xsessions to a backup folder, and made a stumpwm.desktop file containing:

```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=stumpwm
TryExec=stumpwm
Name=StumpWM
Comment=Stump window manager
```

When I switch users, it allows me to choose StumpWM, but the normal lubuntu desktop comes up. Why isn't stump coming up? Thanks in advance!

Edit: I rebooted, now it gives me the error:
:unable to launch "/usr/local/bin/stumpwm" X session ---
"/usr/local/bin/stumpwm" not found; falling back to default session

---

