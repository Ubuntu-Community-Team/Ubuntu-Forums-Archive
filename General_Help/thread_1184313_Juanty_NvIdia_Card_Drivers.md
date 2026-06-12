---
title: "Juanty NvIdia Card Drivers"
date: 2009-06-11
forum: General Help
---

### Post by k_squired on 2009-06-11
Does anyone know where I can get some?  Also, does anyone know if Hardy Heron drivers would work?  I have a GeForce FX 5200.

---

### Post by Magnificence on 2009-06-11
If I'm right you can install it through Add/Remove from the Applications menu.
I'va a NVIDIA graphics card to. I installed it manually. If you go to their website and download a linux driver and install it with your X server closed and root permissions on, it should do it ^^.

---

### Post by maheshasolkar on 2009-06-11
Your best bet is:

  *System -> Administration -> Hardware Drivers*

---

### Post by Magnificence on 2009-06-11
If you need help closing your X server and use root permissions:
First do ctrl+alt+F1.
Then type for GNOME "sudo /etc/init.d/gdm stop", and type your password ;).
Then type "sudo sh [filepath of the driver you downloaded]"
And it should do his work.

---

### Post by k_squired on 2009-06-11
Where might I be able to download these drivers?  I can't find any.

---

### Post by doas777 on 2009-06-12
try installing envyng, and using it to install the drivers.

I seem to recall hearing that the latest restricted drivers excluded a number of ancient nvidia cards (gf5200 is really showing it's age; last one I had was PCI based pre-AGP).

---

### Post by doas777 on 2009-06-12
> **k_squired said:**
> Does anyone know where I can get some?  Also, does anyone know if Hardy Heron drivers would work?  I have a GeForce FX 5200.

ok, first thing, does anything show up under hardware drivers? if you open synaptic, and close it, then go back to hardware drivers, does anything show up? (opening synaptic updates your list of packages available in the repositories).

 you should not try to install a driver compiled for any other system or kernel. if you can't find one for your release, you compile it from source, that you can find on nvidia.com. EnvyNG, basically just downloads the latest driver source online, compiles it on your system, and installs it. you should be able to find it in Add\Remove or Synaptic.

---

