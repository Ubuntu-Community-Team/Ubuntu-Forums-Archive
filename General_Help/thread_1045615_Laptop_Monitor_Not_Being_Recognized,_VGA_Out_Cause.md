---
title: "Laptop Monitor Not Being Recognized, VGA Out Causes Ubuntu Freeze"
date: 2009-01-20
forum: General Help
---

### Post by deathblossom on 2009-01-20
I installed Intrepid on a new laptop today (Sony Vaio NS-240, with Intel GM45 Chipset and ATI Mobility Radeon HD 3430) and due to complications, had to install via safe graphics mode. Having done that though, my laptop won't go any higher than 800x600 and when I try to change it in the screen resolution, it says the monitor is unknown (instead of laptop). I don't know how to install the right graphics drivers (or if that's even the problem), so I'm a bit lost.

Second, plugging an external monitor into the VGA out port causes a total Ubuntu freeze that cannot be recovered from. It happened on the live CD and it's doing the same on the install. Any help on that would be great, please.

---

### Post by Ub1476 on 2009-01-20
You can see if there are any additional drivers in System-Administration-Hardware Drivers, which hopefully will work on your system. :)

All those problems are due to the current (probably radeon or vesa) driver in use. The official driver from ATI usually works better. 

Make sure you have installed updates (System-Administration-Update) before you install the driver from Hardware Drivers.

---

### Post by dcstar on 2009-01-20
> **deathblossom said:**
> I installed Intrepid on a new laptop today (Sony Vaio NS-240, with Intel GM45 Chipset and ATI Mobility Radeon HD 3430) and due to complications, had to install via safe graphics mode. Having done that though, my laptop won't go any higher than 800x600 and when I try to change it in the screen resolution, it says the monitor is unknown (instead of laptop). I don't know how to install the right graphics drivers (or if that's even the problem), so I'm a bit lost.

Second, plugging an external monitor into the VGA out port causes a total Ubuntu freeze that cannot be recovered from. It happened on the live CD and it's doing the same on the install. Any help on that would be great, please.

Look in the Hardware and Laptops forum for anything on your machine.

---

