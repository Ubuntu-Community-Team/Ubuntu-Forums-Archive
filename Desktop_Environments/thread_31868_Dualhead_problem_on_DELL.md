---
title: "Dualhead problem on DELL"
date: 2005-05-05
forum: Desktop Environments
---

### Post by jrohde on 2005-05-05
Hi,

Yesterday I installed Ubuntu on my new DELL Dimension 5000 with nVidia 6800 that has analog as well as digital output.

I also have two DELL LCD monitors, but if I start up with both monitors attached, the monitor that is attached to DVI is black and the other shows a distorted, surrealistic image.

If I unplug the screen attached to the analog output before turning on the pc, everything is fine.

I have checked, that "libxinerama1" is installed. What else is needed?

Thanks,

Jakob

---

### Post by nad on 2005-05-05
man nv or the README for the nvidia driver. man xorg.conf .

---

