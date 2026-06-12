---
title: "Beryl window decorations?"
date: 2007-06-20
forum: Desktop Effects &amp; Customization
---

### Post by luckyd on 2007-06-20
My window decorations just dissapered after a reboot. I don't think I did anything that should have brought this about, they just dissapered.

---

### Post by screaminj3sus on 2007-06-20
[http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/](http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/)

This worked for me, I only had to add the first one Under the device section in xorg.conf

```
Option         "AddARGBGLXVisuals" "True"
```

---

### Post by luckyd on 2007-06-20
Thank you so much, I spent hours trying to fix that before you helped. This should be in a wiki or something...

---

