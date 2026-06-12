---
title: "Vmware Ubuntu XGL and COMPIZ"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Digitallysick on 2006-07-09
How do i set this up? when i try, it seems it never likes my xorg.conf file, but maybe i am not doing something right, is there a wiki for setting this up in vmware?

---

### Post by someusernoob on 2006-07-09
It isnt possible. 

VMware uses his own graphical card (a virtual one), on top of your real graphical card. So you will not be able to install drivers (because the machine does not see your card, but the VMware one) > so you got no 3D support > so there is no way setting up XGL/Compiz properly.

---

