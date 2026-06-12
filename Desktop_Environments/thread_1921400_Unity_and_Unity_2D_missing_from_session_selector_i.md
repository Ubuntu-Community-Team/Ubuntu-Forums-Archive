---
title: "Unity and Unity 2D missing from session selector in LightDM"
date: 2012-02-06
forum: Desktop Environments
---

### Post by blinxwang on 2012-02-06
I recently installed the Cinnamon Desktop environment and after restarting noticed that the Unity and Unity 2D session options had disappeared from LightDM's session selector.
I removed and purged all Cinnamon packages, but that didn't work. So then I reinstalled all unity-related packages to no avail either. I then removed, purged, and then reinstalled unity and unity-2d to no effect. How can this be fixed?

---

### Post by Krytarik on 2012-02-06
First, make sure the "ubuntu-desktop" meta-package is installed:
```
sudo apt-get install ubuntu-desktop
```And if that doesn't fix it, reinstall the package "gnome-session", it includes the files providing those session options:
```
sudo apt-get install --reinstall gnome-session
```Regards.

---

### Post by blinxwang on 2012-02-07
That worked for me. Thanks!

---

### Post by Jelks on 2013-01-27
):P Ive tried the same, and it worked for me (meaning Ubuntu is back on the cog wheel) but it only shows my desktop when it loads up, i dont get the top bar or the unity side bar just a few desktop icons :(

---

