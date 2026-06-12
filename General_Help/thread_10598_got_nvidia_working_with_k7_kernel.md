---
title: "got nvidia working with k7 kernel?"
date: 2005-01-09
forum: General Help
---

### Post by ChrisC on 2005-01-09
I took a vanilla CDROM Ubuntu warty install and first upgraded the kernel to the k7 version, then attempted to install the nvidia drivers.  I tried both the 6111 package via apt and the 6629 package via Nvidia's shell installer.  In the former case, the X server simply failed to start.  In the latter case, attempting to run the Nvidia installer from a console (no X) resulted in it complaining about lacking "cc".  Again, this is a vanilla Ubuntu warty install.  Video card is a GeForce FX5200.  I can get things working fine if I just stick with the 386 kernel.

Does anyone have the nvidia drivers running on a k7 kernel?  I'd be happy to settle for the approved/supported 6111 drivers, I just don't want to have to run a 386 kernel ... I'm sure someone has this working ...

---

### Post by daniels on 2005-01-09
sudo apt-get install linux-restricted-modules-2.6.8.1-3-k7

---

### Post by ChrisC on 2005-01-09
[QUOTE=daniels]sudo apt-get install linux-restricted-modules-2.6.8.1-3-k7[/QUOTE]

OK, thanks, I'll try that.  Perhaps a related question:  what is the difference between 2.6.8.1-3 and 2.6.8.1-4 ?  Both are offered ...

---

### Post by ChrisC on 2005-01-10
[QUOTE=daniels]sudo apt-get install linux-restricted-modules-2.6.8.1-3-k7[/QUOTE]

Thanks, that seems to have worked.  Still wondering about the two kernel versions ... assuming the -4 is a newer package prepare by Ubuntu, why would the -3 still be offered?  Because it's what shipped with the CD?

---

