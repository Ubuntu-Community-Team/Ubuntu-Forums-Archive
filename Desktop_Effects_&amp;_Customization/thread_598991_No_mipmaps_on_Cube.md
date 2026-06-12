---
title: "No mipmaps on Cube"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by UMDGaara on 2007-10-31
Mipmaps work fine for me in every plugin except Cube. Enabling them has no effect and the Cube ends up looking pretty crummy when zoomed out.

I've been using compiz/beryl/compiz-fusion for a while on four systems and they all have the same problem:

Old Dell Pentium 4 with nVidia TI4200 and Gusty Gibbon
Lenovo 3000 N100 with nVidia 7300 GO and Gusty Gibbon
Apple MacBook with Intel 950 and Gusty Gibbon
Custom-built PC with nVidia 7600 GT and Fedora 7

RIght now they all have the same version of Compiz-fusion, the same nVidia driver (except the MacBook), the same options in xorg.conf, and nearly identical plugin settings in CCSM as well as the same launch options. Mipmaps work great on all of them for every plugin except Cube.

Any ideas out there? I thought maybe it had to do with the __GL_YEILD="NOTHING" variable when I launch compiz-fusion but I think that's only for nVidia cards and the MacBook has the same problem.

---

