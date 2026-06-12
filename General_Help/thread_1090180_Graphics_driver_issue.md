---
title: "Graphics driver issue"
date: 2009-03-08
forum: General Help
---

### Post by malfist on 2009-03-08
When I play some of the games that are in the repository (none 3D) I get lines on my screen and strange blurings and discolorings.

The lspci of my graphics card is:
 ```

jerome@jerome-laptop:~$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

Xorg.conf just has configured video device. Any ideas on how to fix this? Pydance is particularly unusable because of this issue.

---

### Post by LegendofTom on 2009-03-08
Try a "sudo dpkg-reconfigure xserver-xorg"

---

### Post by malfist on 2009-03-08
I've already done that, it didn't help. That was the first thing I tried, because intel graphics should be already installed.

---

### Post by malfist on 2009-03-09
I'm running jaunty if that helps any.

---

