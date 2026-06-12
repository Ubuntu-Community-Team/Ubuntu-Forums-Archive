---
title: "mplayer error &gt; Couldn't open /dev/3dfx"
date: 2005-11-22
forum: Desktop Environments
---

### Post by b3nw on 2005-11-22
```
VDec: vo config request - 704 x 400 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
VO: [3dfx] 704x400 => 704x400 Planar YV12
Couldn't open /dev/3dfx

```

at which point it locks up the terminal i'm starting it from.

all i want to do is to be able to play Matroska, but I can't get it working in any player arrg so frusterating.

---

### Post by RAOF on 2005-11-22
You might want to check your mplayer video output options.  It's currently set to 3dfx, which is why it's trying ot open /dev/3dfx.  If you don't **have** a 3dfx, set the video out to something different :)

---

### Post by b3nw on 2005-11-22
got it working, thanks. :)

---

