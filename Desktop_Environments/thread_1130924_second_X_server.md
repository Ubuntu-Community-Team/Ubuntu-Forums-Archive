---
title: "second X server?"
date: 2009-04-20
forum: Desktop Environments
---

### Post by dbcomp on 2009-04-20
Can I run 2 X servers concurrently? ie: local X on F7 (default) and an XDMCP login on F8?  I recall reading about starting a 2nd X server on F8 some time ago, but can't find it again.  

Thanks!

David

---

### Post by linuxfoo on 2009-04-20
Type "startx -- :1" or whichever X-launcher you want (kdm, gdm, ...). The important thing is the Display ":1". If your X launcher doesn't support the display as an argument, set it through the $DISPLAY environment. See [here](http://www.tuxfiles.org/linuxhelp/multiple-x.html).

---

