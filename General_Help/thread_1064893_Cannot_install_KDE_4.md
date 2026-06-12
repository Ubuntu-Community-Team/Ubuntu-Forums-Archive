---
title: "Cannot install KDE 4"
date: 2009-02-09
forum: General Help
---

### Post by Ollock on 2009-02-09
The "KDE4" package comes up with this error:

> KDE4 cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

And I have been totally unable to install kde 4 through any means.  I'm sure it's a hardware problem, but no amount of searching has allowed me to find any kind of BASIC SYSTEM REQUIREMENTS for KDE 4.2.

---

### Post by davideotape on 2009-02-09
Sounds like you have architecture problems. Have you tried going to synaptic and marking "kubuntu-desktop" for installation. This will come up with a list of dependencies which you need, where you just press mark. Then press apply and it should work.

---

### Post by LowSky on 2009-02-09
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
```

---

