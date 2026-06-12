---
title: "Rebuidling xorg.conf"
date: 2006-06-11
forum: Desktop Environments
---

### Post by pratzabrat on 2006-06-11
I have screwed up my xorg conf file, even the backed up ones. How do I rebuild the original and do I have to reinstall my Nvidia graphics card after that. Thanks

---

### Post by MartinG on 2006-06-11
Try the following at a console login:```
sudo dpkg-reconfigure xserver-xorg
```As you work your way through the screens be sure to pick "nvidia" not "nv" at the appropriate point.

---

