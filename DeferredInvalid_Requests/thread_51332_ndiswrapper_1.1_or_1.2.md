---
title: "ndiswrapper 1.1 or 1.2"
date: 2005-07-23
forum: Deferred/Invalid Requests
---

### Post by marcris on 2005-07-23
How about the latest ndiswrapper? The one included with Hoary doesn't work with my wireless card, but 1.1 does. In the process of trying 1.2 after a re-installation of Hoary, but as a newbie this may take a while.

---

### Post by jdong on 2005-07-24
Kernel modules are extremely hard and messy to backport, primarily because all of them are stuck in one linux-restricted-modules deb, which is built from two source packages (one for the whole kernel, another for the restricted stuff).

So, in short, I'm not going to backport NDiswrapper or any other kernel-level updates. NDiswrapper is easy enough to install by hand, if you just get the appropriate linux-headers package for your running kernel :)

---

