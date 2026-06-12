---
title: "Adding a NIC to a system?"
date: 2006-03-10
forum: Desktop Environments
---

### Post by malacoda on 2006-03-10
Quick question:  if I add a new PCI ethernet adapter to my system would Kubuntu detect it automatically during boot or would I have to manually configure?

I'm trying to triple boot XP (until I've weened myself off it), Kubuntu, and PC-BSD but freeBSD doesn't my onboard nVidia nForce based adapter so I'm considering adding a new PCI ethernet adapter to my system.  

I've got a D-link DFE-530TX+ which is supposedly supported by freeBSD but Kubuntu doesn't seem to recongnize it.  I'm not sure if it's unsupported or if I have to manually configure it (bit of a noob in case you can't tell...).

Should it be recognized at start up?  Does anyone know of a NIC that works w/ both Kub and BSD?

regards,
Malac

---

### Post by tabinin on 2006-03-11
I have this same NIC and it is recongized by Ubuntu on my other machine after I enabled it.  If you still have the on-board NIC enabled in the BIOS, you should be able to use both.  One will be eth0 and one will be eth1.  Go to K Menu -> System Settings -> Network Settings.  You may need to access the Administrator Mode.  Assuming you have the on-board adapter still enabled, you should see both listed (eth0 and eth1), but eth1 might not be enabled.  Try enabling it there.

Another option is to disable the on-board NIC in the BIOS and only use the D-Link card.  Then Kubuntu should use use it as the default (eth0) NIC.  Check the System Settings/Network settings to check and see if it is recognized and enabled.

---

### Post by malacoda on 2006-03-12
thanks!

---

