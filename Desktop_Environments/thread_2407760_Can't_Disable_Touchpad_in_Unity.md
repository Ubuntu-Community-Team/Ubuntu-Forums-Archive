---
title: "Can't Disable Touchpad in Unity"
date: 2018-12-08
forum: Desktop Environments
---

### Post by mbott on 2018-12-08
I've been running Ubuntu 18.04/Gnome pretty much since it came out and running it without issue.  Today I "upgraded" 18.04 with Unity and removed Gnome, as I much prefer Unity.  However, it appears that I can no longer disable the touchpad on my Asus laptop.  The laptop is the GL551JW.  

Suggestions anyone?

---

### Post by mc4man on 2018-12-08
Pretty simple,
```
sudo apt install xserver-xorg-input-synaptics
```
(- may or may not require a reboot to now see the setting in System Settings > Mouse & Touchpad (screen

---

### Post by mbott on 2018-12-09
That fixed the issue, but what was interesting was that the control existed prior to the install.  It just didn't do what was requested.  

Thanks!

-- 
Mike

---

