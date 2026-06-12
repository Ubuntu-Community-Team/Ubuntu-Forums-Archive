---
title: "Nvidia no screens."
date: 2007-06-16
forum: Desktop Environments
---

### Post by AJB2K3 on 2007-06-16
After the latest update of X and the nvidea (automatic) im getting the no screens detected message !
1 Has anyone else got this?
2, how do i fix this?

---

### Post by Crafty Kisses on 2007-06-16
> **AJB2K3 said:**
> After the latest update of X and the nvidea (automatic) im getting the no screens detected message !
1 Has anyone else got this?
2, how do i fix this?

You can try this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by AJB2K3 on 2007-06-17
Yeh thanks i found that a few posts down but now im stuck with two duplicate screens because the nvid driver has died.
how do i reinstall driver?

---

### Post by AJB2K3 on 2007-06-17
NVM it had been disabled so i just reenabled the driver.

---

