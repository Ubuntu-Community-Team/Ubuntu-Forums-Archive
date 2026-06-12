---
title: "What could be wrong?"
date: 2007-12-16
forum: Debian
---

### Post by Somenoob on 2007-12-16
I Installed debian-40r1-amd64-kde-CD-1.iso successfully. But X will not start, the error msg states that "there were no screens detected" I have tried to edit xorg.conf like changing to video card driver and such but without any luck.

---

### Post by rsambuca on 2007-12-17
Have you tried reconfiguring your xorg?

dpkg-reconfigure xserver-xorg

---

### Post by jingo811 on 2007-12-19
Try changing your driver to [COLOR="Red"]vesa[/COLOR] in **xorg.conf**, then restart and see if things is still screwed up.

```
...
...

Section "Device"
              Driver "[COLOR="Red"]vesa[/COLOR]"
...
...
```

---

