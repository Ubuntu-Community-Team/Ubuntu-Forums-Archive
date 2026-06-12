---
title: "Change Thunar size?"
date: 2009-03-30
forum: Desktop Environments
---

### Post by Name141 on 2009-03-30
Is it possible to set Thunar's size to a different size?  It always pops up in a little bitty box that I have to resize to see my files (it pops up usually 3 icons per line is all).

---

### Post by catach on 2009-03-31
For me, Thunar remembers the size it was when closed, and opens at that size. However, I have to resize it manually via dragging--the maximize button doesn't work for this.

---

### Post by kerry_s on 2009-03-31
in a terminal:

killall thunar --daemon

now resize thunar and close. it should then remember.

---

### Post by Name141 on 2009-03-31
catach: that worked.

---

