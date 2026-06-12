---
title: "Force resize windows in Gnome/MetaCity"
date: 2005-05-15
forum: Desktop Environments
---

### Post by spiraloid on 2005-05-15
A program I run with wine has problems in that after some operations the maximum window size somehow gets set to 26x7, and I can't resize it at all. Is there a command that I can use to force set a window's geometry or to change or remove the maximum window size hint?

xwininfo -size reports this info:

  Normal window size hints:
      Program supplied location: 24, 929
      Program supplied minimum size: 26 by 7
      Program supplied maximum size: 26 by 7
      Program supplied window gravity: StaticGravity
  No zoom window size hints defined

Thanks.
Mike

---

### Post by freelovemat on 2005-05-16
dunno if that helps you, but you can try to move the window with "alt+click+drag" until you see the edge of the window again and then resize.

---

