---
title: "Changing the greeter to webkit breaks lightdm"
date: 2014-10-30
forum: Desktop Environments
---

### Post by Apathetic012 on 2014-10-30
First of all i'd like to tell that for some weird reason I have no **/etc/lightdm/lightdm.conf**:

```
 ls /etc/lightdm -R/etc/lightdm:
lightdm.conf.d  lightdm-gtk-greeter.conf  lightdm-gtk-greeter-ubuntu.conf  lightdm-webkit-greeter.conf  users.conf


/etc/lightdm/lightdm.conf.d:
10-xubuntu.conf
```

I tried adding **greeter-session=lightdm-webkit-greeter** to **10-xubuntu.conf** and I get stuck on the loading screen with following on the log file:

```
failed to find session configuration lightdm-webkit-greeter
```

although there is a **lightdm-webkit-greeter.conf** file there.

---

