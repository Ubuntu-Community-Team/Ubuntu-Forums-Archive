---
title: "desktop effects could not be enabled"
date: 2007-11-07
forum: Dell  Ubuntu Support
---

### Post by m4cm0 on 2007-11-07
Hi, I have just installed Ubuntu 7.1 onto my Dell inspiron 8200 laptop which has a NVIDIA GeForce2 DDC (generic) Graphics Card.  The problem is that every time i try to activate the extra effects on the desktop background visual effects a window pops up saying that "desktop effects could not be enabled".  Ive checked my restricted drivers and the NVIDIA accelerator graphics driver has been enabled. I have also installed Compiz Config manager, and rebooted, but no luck.  Is it just that my graphics driver unable to process these effects?  Does anyone have the same Laptop.  Your help would be appreciated.

---

### Post by luisromangz on 2007-11-07
Maybe your card is too old and use the nvidia-glx-legacy drivers, which I think doesn't support AIGLX which is the default option for running Compiz. Maybe you should check that, and try to install XGL and run Compiz over it.

---

### Post by m4cm0 on 2007-11-07
Yes that worked well, i installed glx and that did the job. thanks:)

---

### Post by lattmau on 2007-11-09
wait, did you install Xgl or AIGLX?

---

