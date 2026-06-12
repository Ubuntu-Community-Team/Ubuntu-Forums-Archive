---
title: "Poweredge 2950 only 600x800 resolution works with 8.04"
date: 2008-06-17
forum: Desktop Environments
---

### Post by jholzman on 2008-06-17
The ubuntu 8.04 Desktop Version does not allow me to increase screen resolution pass 600 x 800.  Dell support can't find any information on if it will work, or if it does, how to get it to
work.

Dell suggested this. It does not help.  The video chip does not recongize our KVM or monitor:

sudo nano /etc/X11/xorg.conf

change driver from "ati" to "vesa"

Anyone have a fix!:popcorn:

---

