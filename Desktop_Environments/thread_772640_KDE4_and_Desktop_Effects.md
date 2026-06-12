---
title: "KDE4 and Desktop Effects"
date: 2008-04-28
forum: Desktop Environments
---

### Post by lodravah on 2008-04-28
Fooling around with KDE4, and hit another little snag. Slightly optimistic, I turned on "Desktop Effects" using OpenGL and most of the screen went black. Very black.. I could get some windows to come back into focus, and the effects actually worked. When I could see the windows, that is. The background itself was totally black. I know this must be a driver issue, but I am not sure which graphics-card is in the laptop, thus I don't know how to fix this. 

Ideas?

---

### Post by Xiong Chiamiov on 2008-04-29
Boot into recovery mode, and run
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by lunarcloud on 2008-07-09
Nvidia card? Desktop Effects are nicer in 4.1, but still a few issues. Xrender is better.

---

