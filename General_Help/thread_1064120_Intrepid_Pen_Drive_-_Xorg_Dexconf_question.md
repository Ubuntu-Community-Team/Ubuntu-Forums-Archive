---
title: "Intrepid Pen Drive - Xorg Dexconf question"
date: 2009-02-08
forum: General Help
---

### Post by elmagno on 2009-02-08
Just yesterday I installed 8.10 to a pen drive (via the Live menu selection--and I specified persistent), and everything, except one, is absolutely great. But when I reboot, xorg.conf is always rewritten by dexconf and the resulting xorg file is nearly empty, especially no Nvidia driver.

I can run nvidia-settings and generate another good xorg.conf. Then restart the gdm, and Nvidia, Compiz, AWN all load. But on next full boot ... dexconf rewrites the same (nearly) empty xorg.conf.

Here's what I did to get it to boot with the gdm options I wanted: I finally (simply) renamed dexconf in usr/bin. Now it all boots and works as I think it should. But I really don't know what side effects I might be in for by bypassing dexconf . . . . All thoughts very welcome. Thanks.

---

