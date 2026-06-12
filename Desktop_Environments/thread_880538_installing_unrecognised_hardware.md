---
title: "installing unrecognised hardware"
date: 2008-08-05
forum: Desktop Environments
---

### Post by amado738 on 2008-08-05
I have some hardware that ubuntu does not recognise I have a analogue tv tuner card and I'am not sure how to install it in ubuntu. Is there a simple way or do I need special software to install it. it was a cheapo one so only came with windows software ( surprise surprise! ). Does ubuntu have a simple system like windows "add new hardware wizard" or equivalent. 
thank you in advance!

---

### Post by hyper_ch on 2008-08-05
> **amado738 said:**
> Does ubuntu have a simple system like windows "add new hardware wizard" or equivalent.
Generally: No

Either hardware is directly support because it has drivers in the kernel or it isn't. Best guess is to google for that tv card. Maybe the producer have drivers, maybe you find a solution in the world wide web.

---

### Post by ryanhaigh on 2008-08-05
Assuming its a PCI device you might want to try this page: 
[http://kmuto.jp/debian/hcl/index.cgi](http://kmuto.jp/debian/hcl/index.cgi)

It's a great way to determine whether your card is supported. The output of lspci is also a good thing to use when generally searching if your hardware can be used on Linux.

---

