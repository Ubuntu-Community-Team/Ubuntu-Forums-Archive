---
title: "Icon image as a question mark in launch bar"
date: 2013-05-30
forum: Desktop Environments
---

### Post by veledrom on 2013-05-30
Hi,

I just extracted Navicat from tar.gz into /home folder. When I run it, a question mark appears on launchbar on the left instead of navicat's icon. Note: Initial run shows the original icon but suddenly becomes question mark.

Any idea?

Ubuntu 12.04

Thanks

---

### Post by Frogs Hair on 2013-05-30
There are a couple of possible causes . Your current icon set has no icon and the application is defaulting to the current icon set and not to the location of the original application icon. If you check in File System/Computer usr/share/applications you can see what if any the icon appears there. Another possible location for the original icon maybe pixmaps.

---

