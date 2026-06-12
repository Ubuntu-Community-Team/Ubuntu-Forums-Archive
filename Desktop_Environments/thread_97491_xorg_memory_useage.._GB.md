---
title: "xorg memory useage.. GB?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by jaykup on 2005-12-01
Ive seen a few posts with people complaining that Xorg is using 150, or 300 mb of memory, and how slow their systems are going..

My Xorg is using 1GB of memory currently, and I've seen it higher..  yeah I've got a few windows open, but this is crazy!  Ive actually seen it at around 2.1GB at times.. and I'm not running anything but the Aqua mac theme from gnomelooks

any ideas?

---

### Post by magnusbb on 2005-12-01
Then maybe the theme is the problem.

I would recommend installing a cute little program called **xrestop**. It shows the x-server resources used by the different clients. It will for example show you how much Firefox puts into Xorg for un-compressed images and so on. There you will be able to locate the problem.

Currently my Firefox 1.5 with 4 tabs open and some images uses 14 MB in the the X-server. That's not bad, it was worse with the former Firefox.

---

### Post by jaykup on 2005-12-02
Its GAIM, its causing 1GB memory usage if left on overnight, and using 100% CPU usage (on one of the processors)

---

