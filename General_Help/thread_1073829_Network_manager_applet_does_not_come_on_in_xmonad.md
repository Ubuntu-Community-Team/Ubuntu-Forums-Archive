---
title: "Network manager applet does not come on in xmonad"
date: 2009-02-18
forum: General Help
---

### Post by johnnyxxxcakes on 2009-02-18
I've installed and changed my session at the login screen to the xmonad window manager. When everything boots up all fine, I don't have internet. I think this is because the network manager applet which is in GNOME doesn't startup with xmonad. How do I get this working so I get my wireless internet to work?

I've already tried typing "sudo /etc/init.d/networking restart", "network-manager-gnome", and "network-manager-applet" from within the terminal, but nothing seems to work.

---

### Post by kerry_s on 2009-02-18
editor ~/.xinitrc

```
#!/bin/sh
nm-applet &

exec xmonad
```

---

### Post by johnnyxxxcakes on 2009-02-19
Thank you! That worked perfectly.

---

