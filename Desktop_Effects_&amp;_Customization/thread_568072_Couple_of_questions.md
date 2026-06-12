---
title: "Couple of questions"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by nawitus on 2007-10-05
I'm using Ubuntu 7.04

1. How can I disable the effect you see when you minize any window? I'm talking about those black/white rectangles.

2. Is there a way to change the large Nvidia startup pic that is shown for like a second when you boot? It's annoying. I used the Envy script to install my drivers.

3. Can I change the small ubuntu logo that is besides the "Applications" menu in the panel?

---

### Post by FuturePilot on 2007-10-05
I'm not really sure on 1 and 3 but to disable the Nvidia splash screen you need to edit your xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```
Go down to where it says Section "Device"
and add this 
```
Option       "NoLogo"      "True"
```

---

### Post by nawitus on 2007-10-05
Thanks.

---

