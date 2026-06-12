---
title: "Have you been blacklisted?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Amaranth on 2007-10-19
Trying to run compiz and getting the following output?```
Blacklisted PCIID '8086:2972' found
```
This means your video card has been blacklisted due to driver issues. This applies to some Radeon Mobility cards, Radeon rv350 and rv450 cards, and the Intel 965 (X3000, X3100). You can dodge that blacklist (at your own peril) with the following:```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

If you do this please do not post about any issues you have with stability or video playback problems, that's why your card was blacklisted in the first place.

---

