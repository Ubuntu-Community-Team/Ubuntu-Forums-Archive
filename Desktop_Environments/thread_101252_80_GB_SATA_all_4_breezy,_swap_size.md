---
title: "80 GB SATA all 4 breezy, swap size ?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by rfruth on 2005-12-09
About to install Breezy here on a plain ole P4 box (1 80 GB SATA drive, 512  RAM, 128 ATI video card) no dual boot (breezy can have all 80 GB), how big should the /swap size be for max performance ? The docs say put in 2*n Mb swap, what do you say, a little bigger/smaller or just use the default size :rolleyes:

---

### Post by earobinson on 2005-12-09
the swap space is virtual memory it really depends on what programs you are going to be running.

I run the forums, bit torrents, gaim, rhythmbox, rbscrobler, gnome, open office All at once, I have a gig of mem and a 2 gig of swap space. My swap space never gets used. But HD's are cheap and its nice to know I have it.

IMO its always good to have at least a gig of swap space. But if you never use it i guess its space going to waist. You can always resize your swap space ones linux is installed, for that reason I would go bigger rather than smaller and If you find you dont use it then shrink it using gparted.

NOTE: I would go bigger and shrink rather than smaller and make bigger because you cant go wrong with big.

Hope this helps.

*extra points before searching the docs before your post*

---

### Post by mad_phoenix on 2005-12-09
Just make sure it's in an LVM group and it won't matter ;).

---

