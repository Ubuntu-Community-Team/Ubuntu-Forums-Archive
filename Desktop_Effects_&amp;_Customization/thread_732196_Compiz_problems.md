---
title: "Compiz problems"
date: 2008-03-22
forum: Desktop Effects &amp; Customization
---

### Post by cmstackar on 2008-03-22
Hi! Well, i installed compiz yesterday and it worked fine, until just now. The cube and wiggly windows are gone, and it seems that advanced appearance wizard or whatever has disappeared. Also, yesterday, i noticed that with compiz installed, i couldn't log off, but could shut down just fine. I'm using an ATI 2600pro, on Ubuntu 7.10 (32 bit) Any help is greatly appreciated. The tops of windows are still transparent, and when i minimize something, it still uses that effect.

---

### Post by erginemr on 2008-03-22
Hi. A few questions:

1. how did you install compiz? From Ubuntu repositories or from somewhere else?

2. What is the compiz version you have been using? From a terminal:
```
dpkg -l | grep compiz-core
```
```
dpkg -l | grep compizconfig-settings-manager
```

3. What is the outcome of the following from a terminal:
```
ccsm
```
(N.B. ccsm is the advanced appearance wizard)

4. Is your 3-D still enabled:
```
glxinfo | grep -i direct
```

---

### Post by cmstackar on 2008-03-22
It's okay, my friend got back from vacation and was able to help me. Thanks anyway.

---

