---
title: "Can't modprobe nvidia_new"
date: 2009-04-15
forum: General Help
---

### Post by DJonsson2008 on 2009-04-15
I've got 2 machines here Ubuntu Hardy latest updates,
one machine sees the Nvidia proprietary drivers the
other does not.

If I attempt one machine to modeprobe nvidea_new i get
the following..  

$ modprobe nvidia_new
  Not loading nvidia_new module; not used in /etc/X11/xorg.conf

The other machine loads it fine. Now I've attempted to match
the directories of both machines for listings of nvidia and
nvidia_new and they both seem to match, I'm wondering why 
modprobe does not see nvidia_new in this instance and what
I can do to find out why and what is missing?

Linux 2.6.24-23-386 GNU/Linux

root@quetzl:~# locate nvidia_new
/lib/linux-restricted-modules/.nvidia_new_installed
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/nv-i2c.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/nv-kernel.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/nv-vm.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/nv.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/nvacpi.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/nvidia.mod.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/os-agp.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/os-interface.o
/lib/linux-restricted-modules/2.6.24-23-generic/nvidia_new/os-registry.o

---

### Post by DJonsson2008 on 2009-04-16
Towards finding why modprobe won't load this module that according
to locate is on the machine...Could anybody suggest a whitepapers 
links about ;

* How Unbuntu/Linux loads and handles modules?

* What are the general debugging steps when modprobe does
  not load a driver installed from the Ubuntu repositoriies.

---

### Post by DJonsson2008 on 2009-04-16
The other bit of evidence on this is from var/logs/Xorg.0.log

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

---

