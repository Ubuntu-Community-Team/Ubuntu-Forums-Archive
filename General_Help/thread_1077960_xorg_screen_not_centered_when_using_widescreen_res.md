---
title: "xorg screen not centered when using widescreen resolution"
date: 2009-02-22
forum: General Help
---

### Post by chocolatetoothpaste on 2009-02-22
Hi all,
  I have my old laptop hooked up to my HDTV as a HTPC, and I'm using 1360x768 resolution (16:9).  The problem is, at this resolution, there is a black margin on the left of the screen, and part of my desktop is off the screen on the right.  It seems like it's just a matter of the screen not being centered.  Are there any Xorg wizards who know how to fix this screen offset?   Thanks

---

### Post by chocolatetoothpaste on 2009-03-09
*bump*

---

### Post by davidryder on 2009-03-09
Just to get you started, have you tried using different drivers?

```
dpkg-reconfigure xserver-xorg
```

---

### Post by chocolatetoothpaste on 2009-03-16
I tried it again just now for good measure, same result: the screen is shifter about 100px to the right.

---

