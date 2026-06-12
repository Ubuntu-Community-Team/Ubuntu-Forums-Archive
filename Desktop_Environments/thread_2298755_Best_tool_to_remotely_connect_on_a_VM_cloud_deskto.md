---
title: "Best tool to remotely connect on a VM cloud desktop"
date: 2015-10-13
forum: Desktop Environments
---

### Post by metan on 2015-10-13
Hi all

I was testing the last time this demo interface : [http://tour.ubuntu-fr.org/fr/index.html](http://tour.ubuntu-fr.org/fr/index.html)

- and was wondering which technology is used ? I mean, instead of using this ugly XRDP, and be required to use XFCE because gnome desktop is too slow when I remote access to the VM cloud, what kind of techno or tool I could use 
-  what is the tool / techno used for tour.ubuntu-fr.org ?
- what do you recommend?

THANKS a lot for your feedback/

---

### Post by TheFu on 2015-10-13
That isn't a real Ubuntu system. It is a manually created javascript program.
For remote access to cloud servers, 99.99999% of us use ssh. This is a text interface.

If you must have a GUI and are willing to use that amount of bandwidth, check out x2go. There is a client and a server.  It doesn't work with any desktop that requires 3D accel graphics.  Use LXDE, XFCE or a plain openbox WM.   Follow the x2go  website instructions, be certain to use their PPA. It works over ssh too.  Lots of similar question in these forums, BTW. x2go feels about 2-3x faster than the other alternatives.

---

### Post by metan on 2015-10-13
Thanks man its clear, will try x2go to see what it gives.

---

