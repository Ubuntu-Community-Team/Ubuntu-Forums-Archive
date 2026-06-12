---
title: "Ubuntu hangs on boot"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by JFASI on 2007-08-25
Dell Inspiron D610, Pentium M 1.8, 750 RAM, NVidia, Edgy, 2.6.20-16.

Occasionally, when I try to start up Ubuntu, the loading screen appears, and the progress bar goes to up to the third little line, the hard drive light sputters, and the boot hangs. This happened both on 2.6.20-15 and 2.6.20-16, after I upgraded it. When I boot it in recovery mode, it stops saying: 

ACPI PCI Interrupt 0000:03:03.0[A] -> GSI (level, low) -> IRQ

Is there any way to force the regular starup to go into verbose mode?

---

### Post by ntom-taylor on 2007-08-25
Not much help im afraid bu yes you can do it, you have to edit some file. try searching for how to change the splash image, the file that specifies this is the one u need to change.

---

### Post by fscodelaro on 2007-09-05
See if this helps:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell#head-c2ca55256bf844a55a2c36d933bba9743b6b2ed0](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell#head-c2ca55256bf844a55a2c36d933bba9743b6b2ed0)

I'm running Feisty updated on a D610 (integrated graphics) and everything works fine.

---

