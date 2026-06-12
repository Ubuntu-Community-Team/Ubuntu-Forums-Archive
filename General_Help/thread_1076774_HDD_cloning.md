---
title: "HDD cloning"
date: 2009-02-21
forum: General Help
---

### Post by Snow986 on 2009-02-21
So I got a new HDD for my laptop which is a dual boot vista/ubuntu 8.10 and I am still debating whether I want to fresh install everything to my new HDD or just clone my current drive. Anyways my question is, if I clone, either from the windows side or the linux side, will it clone my dual boot correctly?  Should I have the new disc formatted before copying the image? If this has been answered before, feel free to point me there.

Thanks

-Matt

---

### Post by lukjad on 2009-02-21
From what I understand about cloning, it copies everything. If I were you I would, just to be on the safe side, do it from the linux side, or from a live CD or 3rd party utility.

---

### Post by dorkdork777 on 2009-02-21
Yes, do it from a LiveCD. And if you copy the *entire* disc, in other words everything on it (including MBR), then yes, it will copy your dual boot setup perfectly.

---

### Post by nowhere@cox.net on 2009-02-27
What package do you use to do this?

I'm thinking I should just be able to ```
dd if=/dev/hdb of=/dev/hda
``` after physically stuffing the old drive into an enclosure (or in my case the ultrabay) yah?

Thanks!

---

