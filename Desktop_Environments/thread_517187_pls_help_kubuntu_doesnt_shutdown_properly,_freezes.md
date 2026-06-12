---
title: "pls help: kubuntu doesnt shutdown properly, freezes during shutdown"
date: 2007-08-04
forum: Desktop Environments
---

### Post by cyneuron on 2007-08-04
hello there

first of all, i am not a newbie. i have good knowledge of linux. have worked with lotta distro.

i personally like Kubuntu. two reasons : its based on ubuntu, secondly, its not gnome .

i have kubuntu feisty installed on my acer aspire laptop with intel 915 chipset. all things work fine. i just had to upgrade x org video driver for intel chipsets from i810 installed to latest available for i915 and i945 chipset to get the correct resolution 1280 * 800

but my system frequently doesn't shutdowns properly. it just freezes during shutting down. then i have to turn it off manually from power button. an it happens quite frequently, though not always, surprisingly.

there was no such problem in ubuntu with same configuration. so i think it is related to kde only.

one thing i suspect in this : when i open kwrite from terminal it shows some error messages regarding x org configuration :

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

may be these are indicating to some problem to x org configuration.

and may be shutdown problem is related to that.

whatever is the case.

please help me to find out the problem.

---

### Post by luisromangz on 2007-08-04
Is it able to finish your KDE session properly, or it locks berfore going back to KDM?

---

### Post by cyneuron on 2007-08-04
i cant tell exactly. it just goes into a blank screen.

---

