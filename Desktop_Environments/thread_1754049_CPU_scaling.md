---
title: "CPU scaling"
date: 2011-05-09
forum: Desktop Environments
---

### Post by leo72 on 2011-05-09
After several years with Ubuntu, I installed Xubuntu 11.04 on my 4 y.o. laptop. But I cannot change the CPU clock.
I've tried to use xfce4-cpufreq-applet but I can only look at the governor in use: I cannot change nothing.
I also tried to use xfce-governor-applet but this one doesn't start into the panel...

How can I manage the CPU scaling? Under Gnome I was able to do that, so I'm sure my laptop can do that (P4-M 1.8 GHz).

---

### Post by Flightmare on 2011-05-09
Make sure your correct CPU module is loaded with
*sudo modprobe p4_clockmod*

For more information on the manual approach:
[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

---

### Post by leo72 on 2011-05-09
Uhm... I get:
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.38-8-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): Device or resource busy

That doesn't sound good, isn't it? :(

I'll get a look at the link you posted...

But it's strange. I've never had problems in the past: I used Ubuntu, openSuse, Arch, and several other distros... :confused:

EDIT:
maybe it's all right because my laptop uses Centrino chipset so I don't have to use p4_clockmod.

---

