---
title: "Compaq v2000 Laptop over heating!"
date: 2009-01-14
forum: General Help
---

### Post by carbm1 on 2009-01-14
I recently acquired a Compaq V2000 laptop. AMD Turion 64 ML-34. I immediately installed Ubuntu 8.10 64 bit. I also have the same problem in 8.04 32 bit.  When I first turn on the laptop the cooling fan spins up but once I boot into Ubuntu the fan turns off and will never turn back on. Works fine in Windows XP and in WinPE. 

I think this has something to do with ACPI and /proc/acpi/thermal_zone/THRM/trip_points. However apparently in newer kernels you cannot change these settings. 

I have nothing listed under /proc/acpi/fan or I could tell it to turn back on.  I have installed lmsensors but nothing showed up for sensors for the fan, only CPU temp and hard drive temp.

When I try and use kernel commands acpi=off or noacpi Gnome fails to start.  It simply hangs a black screen.  Fan stays on though.

I have updated to the latest BIOS available from the Compaq website.

Any help is greatly appreciated!

Thanks,

Craig

---

