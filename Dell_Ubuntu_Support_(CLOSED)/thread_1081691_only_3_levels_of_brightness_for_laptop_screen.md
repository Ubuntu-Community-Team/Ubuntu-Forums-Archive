---
title: "only 3 levels of brightness for laptop screen"
date: 2009-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2009-02-26
With Ubuntu (8.04) there are only 3 levels of screen brightness for my XPS M1330 laptop:  0%, 50%, and 100%.  Under Vista, there are more levels.  Is there a parameter to set for Ubuntu that allows more levels of screen brightness?

*TimDaniels*

---

### Post by biocorp on 2009-02-26
put "blacklist video" in /etc/modprobe.d/blacklist

---

### Post by TimDaniels on 2009-02-27
> **biocorp said:**
> put "blacklist video" in /etc/modprobe.d/blacklist

Thank you!  Now there are 7 levels of brightness instead of just 3.

*TimDaniels*

---

### Post by geoffm on 2009-03-03
I was using the workaround of adjusting brightness with the "brightness applet" in the gnome panel.
I'll try the blacklist video though!

---

### Post by geoffm on 2009-03-04
Will that work to bring down the increment when using the keyboard volume up / volume down buttons?

---

