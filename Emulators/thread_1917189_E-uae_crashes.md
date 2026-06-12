---
title: "E-uae crashes"
date: 2012-01-29
forum: Emulators
---

### Post by svin83 on 2012-01-29
Hi! I'm running Ubuntu 11.10 x64 and I've installed e-uae from repo, but when I tried to start it from terminal, it always terminates with a segfault :(

When started from icon in launcher it worked sometimes at first, but now it won't work from icon either.

Any hints on what to do?

---

### Post by FrodeSolheim on 2012-05-01
> **svin83 said:**
> Hi! I'm running Ubuntu 11.10 x64 and I've installed e-uae from repo, but when I tried to start it from terminal, it always terminates with a segfault :(

When started from icon in launcher it worked sometimes at first, but now it won't work from icon either.

Any hints on what to do?

This does not exactly answer your question, but I would like to recommend trying FS-UAE, which I'm the author of. It  has an updated emulation core from WinUAE, and the video/audio/input  layer is rewritten from scratch, so it may work better for you than  E-UAE. Also, it is an activate project and will receive fixes if problems are found.

I run it myself on Ubuntu :smile:   (just note that with 12.04 and 3D-accelerated desktop, you may need to  run FS-UAE in fullscreen or with the option --video-sync=off to get  good performance due to a Compiz issue).

If you try it out and have any problems, just let me know.

[http://fengestad.no/wp/fs-uae](http://fengestad.no/wp/fs-uae) (I provide precompiled Ubuntu/Debian debs).

---

### Post by corrosion on 2012-05-06
The bug has been reported:
[https://bugs.launchpad.net/ubuntu/+source/e-uae/+bug/848315]("https://bugs.launchpad.net/ubuntu/+source/e-uae/+bug/848315")

---

