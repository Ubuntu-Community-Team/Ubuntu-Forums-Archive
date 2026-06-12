---
title: "Disable onboard Radeon 7000/VE?"
date: 2008-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mapasano on 2008-09-10
I have a Dell Poweredge 1800 running Ubuntu Hardy.  It has an onboard Radeon 7000/VE that I need to disable so the box can see the new PCI NVIDIA GeForce 6200 I installed.  Every time I try to boot with the card installed it hangs.  I tried blacklisting by the following:

sudo gedit /etc/modprobe.d/blacklist

then added, saved, and rebooted: 

blacklist intel_agp
blacklist agpgart

Still no luck.  Not sure if I need to target another driver.

My bios does not provide for the ability to disable the bios.

Anyone have any ideas?

Thanks

---

### Post by Cresho on 2008-09-10
In the bios, look for onboard graphics card.  Disable it.  THen your nvidia will run.

---

### Post by Mapasano on 2008-09-10
I should have added this to the original post but my bios does not give me the option to disable the embedded video.  Any other ideas?

Thanks

---

### Post by user11 on 2009-07-07
I have the same problem, I would love to now how we can disable the on-board video chip, or at least pick which one to use like Windows allows us. It stinks having to run XP to use the drivers, especially for something silly like this.

---

