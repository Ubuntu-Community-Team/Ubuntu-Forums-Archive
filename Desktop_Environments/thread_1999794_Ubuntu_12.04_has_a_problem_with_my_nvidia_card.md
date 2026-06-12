---
title: "Ubuntu 12.04 has a problem with my nvidia card"
date: 2012-06-08
forum: Desktop Environments
---

### Post by ronaldv on 2012-06-08
Hi,

I believe Ubuntu 12.04 (32bits) has a big problem with nvidia cards. Since upgrade to it my system did not boot normally anymore, and only with low resolutions.

I tried quite a lot, like switching between the nvidia, nouveau and vesa driver but only the vesa driver worked. For the other drivers it mentioned that the card (VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GT] (rev a1)) was not supported.

To be sure that it was a ubuntu-12.04-32bits problem I:
- booted from the 12.04-32bits cd: same problem
- booted a 11.04-64bits partition on my hd: no problem
- booted from the 12.04-54bits cd: no problem

I will add my xorg.log file to this post for more detail. You will notice that the kernel is trying to load several drivers but keeps failing.

I hope somebody from Ubuntu will look into this problem.

---

