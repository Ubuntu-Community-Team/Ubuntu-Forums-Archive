---
title: "VNC connection to Shared Gnome Desktop 20.04"
date: 2020-06-10
forum: Desktop Environments
---

### Post by gourmetsaint on 2020-06-10
Using TightVNC to try to connect to shared desktop. Get "No security types supported." Same error with every Android and Windows client I can find. Is there catchup required for VNC clients. Any ETA on a fix?

---

### Post by ubname on 2020-06-11
I don't think it will be fixed, only way I found was to disable encryption on the gnome desktop for the connection, so the connection will not be secure

```
gsettings set org.gnome.Vino require-encryption false
```

---

### Post by gourmetsaint on 2020-06-22
Thanks heaps!!

---

