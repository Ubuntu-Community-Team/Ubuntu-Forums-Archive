---
title: "xinerama does not work with new ati/radeon video driver"
date: 2008-01-04
forum: Desktop Environments
---

### Post by hdoria on 2008-01-04
Im trying to setup xinerama e dual head on my computer. I have a ati radeon 9200pro and im using the latest radeon/ati video drivers. xorg.conf seems ok, but dualhead does not work. Everytime i uncomment the xinerama lines X does not work.

When i use a old ati driver (6.6.3-2) X and xinerama works.

Is it a driver problem or am i missing some configuration options for the newer driver?

```
# lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

# dpkg -l | grep -i xserver-xorg-video-ati
ii  xserver-xorg-video-ati                     1:6.6.3-2ubuntu6                     X.Org X server -- ATI display driver
```

---

