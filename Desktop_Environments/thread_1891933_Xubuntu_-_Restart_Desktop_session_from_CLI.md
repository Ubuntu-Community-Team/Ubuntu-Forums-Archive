---
title: "Xubuntu - Restart Desktop session from CLI?"
date: 2011-12-06
forum: Desktop Environments
---

### Post by sr_guy on 2011-12-06
I'm running my PBX (Asterisk + FreePBX) and my multimedia (XBMC) from one box. All conncected to a TV. Running Xubuntu 11.10.

In a regular Ubuntu distro I could type in (as root) service gdm restart to restart my whole desktop session if needed without having to reboot. Is there an equivalent command in Xubuntu that will restart X?

---

### Post by Toz on 2011-12-06
Xubuntu (and ubuntu) version 11.10 have switched from gdm to lightdm. You can try:
```
sudo service lightdm restart
```

---

