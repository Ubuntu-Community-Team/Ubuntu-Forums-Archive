---
title: "Changing video mode from command line"
date: 2006-02-14
forum: Desktop Environments
---

### Post by jsbake2 on 2006-02-14
I am running Ubuntu 5.10 from Virtual PC and having some issues with the video. I am able to load the system but it is completely unusable, I probably have the wrong resolution set. The easiest approach would be to to re-install the system but I would rather learn something in the process. What are the commands to change the resolution/refresh/depth from the command line in Ubuntu.
Jason

---

### Post by anllogui on 2006-02-14
Try:
dpkg-reconfigure xserver-xorg

I don't know sure the name of the package, but is like it. This is the debian way to do it.

---

