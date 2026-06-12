---
title: "vnc problem - incorrect text background color"
date: 2006-03-15
forum: Desktop Environments
---

### Post by mkent on 2006-03-15
I'm using vncserver on my Ubuntu desktop, and connecting to it with RealVNC vncviewer on my Windows laptop. Everything works fine except for one thing...

I get a weird blueish background color on all the text. Everything else displays properly and the colors look fine, but all the text is messed up.

I'm using all of the default options for vncserver except geometry=1400x1000. Anyone else seen a problem like this?

---

### Post by mkent on 2006-03-15
I just tried forwarding a window over x and the fonts appeared fine. They still look weird over vnc though.

---

### Post by mkent on 2006-03-15
well, i fixed it indirectly by using tightvnc instead of realvnc. everything works fine and dandy now.

---

