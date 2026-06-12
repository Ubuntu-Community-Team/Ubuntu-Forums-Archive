---
title: "Trouble with the Nvidia driver"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by Neurasthenic on 2007-06-09
Hi,
I'm running Ubuntu 7.04 on a slightly dated machine, with an AMD AXP1800+ and integrated Geforce 4 MX graphics. My problem is, after enabling the unsupported Nvidia 3d driver through the Restricted Hardware menu, 3d games do not work correctly.

For example, Chromium starts up and displays a black screen.
Armagetron too displays a black screen, although I've noticed that if I hit some buttons and move the mouse I can see some very faint traces of the game being played (kind of a partial wireframe view, though I'm guessing the wireframe look is part of the game - I haven't been able to actually see what it looks like normally).

Also, after enabling the driver, everything else seems to work well. 3d screensavers run smoothly, as well as the desktop effects (despite the bugs). If it helps any, I did try starting Chromium before enabling the 3d driver and I could see just fine, but the framerate was too low - so the game did work initially.

---

### Post by Sockerdrickan on 2007-06-09
GeForce MX isn't supportet, use legacy

---

### Post by Neurasthenic on 2007-06-09
I was wondering if that would be a problem, I figured my card could be too old.
I'm very new at this whole thing, and the only reason I was able to enable this driver was because it was right in front of my face in a nice graphical interface - how would I go about installing the legacy driver?

---

### Post by Sockerdrickan on 2007-06-09
I think it's in the repos, or you could download it from [www.nvidia.com](www.nvidia.com)

---

### Post by Jarn on 2007-06-09
Remove whichever one the the GUI installed (not sure how you would do that as I use Kubuntu and we're not special enough to get a Restricted Hardware menu) and then, from a terminal:```
apt-get install nvidia-glx-legacy
```

---

