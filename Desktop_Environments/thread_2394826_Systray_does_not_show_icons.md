---
title: "Systray does not show icons"
date: 2018-06-22
forum: Desktop Environments
---

### Post by gdesilva on 2018-06-22
Running Ubuntu Studio 18.04 and notice that applications such as vlc and Dropbox do not show their icons on the systray. 

Can some one please tell me where systray looks for app icons?

Thanks

---

### Post by gdesilva on 2018-06-22
UPDATE: Manage to recover the dropbox icon by installing sni-qt as per [https://askubuntu.com/questions/456950/system-tray-icons-disappeared-after-upgrading-ubuntu](https://askubuntu.com/questions/456950/system-tray-icons-disappeared-after-upgrading-ubuntu)

However, the vlc icon is still shown with a 'not found' icon.

---

### Post by gdesilva on 2018-06-22
The solution was found in [https://forum.xfce.org/viewtopic.php?id=8799](https://forum.xfce.org/viewtopic.php?id=8799)

Essentially, stop autostarting indicator application or uninstalling indicator application fixed issues with dropbox and vlc.

---

