---
title: "Force a Resolution Change"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Transport Man on 2006-09-23
I Installed Ubunutu with the Alternate install CD however I did not set the resolution when I began the installer now my screen is set to a resolution that my monitor can not handle. I am wondering if there is a command that I can use in the recovery mode to force the resolution to be set at 800x600 with 32 bit color.

---

### Post by FizDev on 2006-09-23
Type this
```
sudo dpkg-reconfigure xserver-xorg
```

Just set everything as you want, and everything should work afterward.

EDIT:
You can also modify manually your xorg.conf :)

---

