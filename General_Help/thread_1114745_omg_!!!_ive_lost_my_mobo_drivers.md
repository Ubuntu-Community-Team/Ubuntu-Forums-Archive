---
title: "omg !!! ive lost my mobo drivers"
date: 2009-04-03
forum: General Help
---

### Post by john@proficientpc on 2009-04-03
yeah i was installing virtualbox and had to go into synaptic to install a kernel  and then restart when i rebooted back in to Ubuntu i lost every thing my usb wifi, and mobo's nvidia drivers sound plez help !!!!!

---

### Post by DagMan on 2009-04-03
you likely just need to boot into the old kernel if you can.  You'd hit escape during boot to get to the grub menu and see if theres more than one kernel there. for example a generic one, then use the arrow keys to select it and hit enter.

---

### Post by john@proficientpc on 2009-04-03
yeah im doing that now !! and i get wifi back and sound but graphics card is still not in the hardware drivers. also i don't want to have to keep hitting esc when i boot up my comp

---

### Post by john@proficientpc on 2009-04-03
im just going to reinstall Ubuntu 8.04

---

### Post by 3rdalbum on 2009-04-03
If you manually compile any drivers, then certain kernel updates will not be compatible with the old drivers. You would need to recompile the drivers again if you get a new kernel.

Stick with the repositories for your Nvidia driver and wireless driver if possible, and this will prevent the problem. Or don't install kernel updates. (use Synaptic to "lock version" on your current kernel).

---

