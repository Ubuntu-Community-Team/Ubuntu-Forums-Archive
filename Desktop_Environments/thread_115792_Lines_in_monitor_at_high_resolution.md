---
title: "Lines in monitor at high resolution"
date: 2006-01-11
forum: Desktop Environments
---

### Post by kenquad on 2006-01-11
Hi all:

I have a brand-new Acer AL1715 LCD monitor.  Whenever I try to set the resolution higher and 1024x768 - including on startup as the default is higher - fuzzy vertical lines appear in the screen.  I've never done any xorg configuration and I don't want to end up with "fried monitor a la Linux" (or is that even possible with an LCD?).  ???

Thanks:D

---

### Post by shakin on 2006-01-11
[QUOTE=kenquad]Hi all:

I have a brand-new Acer AL1715 LCD monitor.  Whenever I try to set the resolution higher and 1024x768 - including on startup as the default is higher - fuzzy vertical lines appear in the screen.  I've never done any xorg configuration and I don't want to end up with "fried monitor a la Linux" (or is that even possible with an LCD?).  ???

Thanks:D[/QUOTE]

Check what refresh rate it's running at. It shouldn't be any higher than 75Hz for that monitor and might even be lower. Try as low as 60Hz. To do this you will need a line in your /etc/X11/xorg.conf file similar to the following:

```

VertRefresh     60

```

---

### Post by kenquad on 2006-01-13
Believe it or not, the problem was a lack of RAM.  Upgrading to 512 MB fixed it!

---

