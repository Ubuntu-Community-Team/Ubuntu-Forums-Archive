---
title: "had to rebuild and reinstall ati driver package"
date: 2009-04-08
forum: General Help
---

### Post by sdowney717 on 2009-04-08
a system update came thru a couple days ago and I had to rebuild the ATI driver package and do a reinstall.
the computer had slowed down and the video response was terrible.
glxinfo had said direct rendering yes but glxgears was running 90% slower than it should have done. 
a simple reinstall of what I had built prior gave a black screen at reboot.
So I went to the root command prompt and executed the rebuild.
It is all working nicely again.
it is basically these steps in the folder where you put the ATI driver download
from terminal run

./atidriverinstallername --buildpkg Ubuntu/intrepid
dpkg -i *.deb
aticonfig --initial

---

### Post by Yashiro on 2009-04-08
The dkms kernel module build failed for some reason. Maybe your kernel headers were missing? Dunno.

If you try to install over a system that is broken in this way it will crash at the GDM on reboot. Been there, have the tshirt.

So the fix as you discovered is to boot as root (no gdm init)
And perform the install again.

---

