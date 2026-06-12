---
title: "Compiz on Nvidia GeForce MX 4000"
date: 2009-02-14
forum: General Help
---

### Post by iman1000000 on 2009-02-14
I cannot get compiz to run on my Nvidia GeForce MX 4000.
I have tried to install the drivers but they don't turn up on the hardware drivers screen.
My output from compiz-check is:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV18 [GeForce4 MX 4000] (rev a4)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) n

```
Does anyone know what the problem is?

---

### Post by iman1000000 on 2009-02-14
I tried running Nvidia X Server Settings and it told me to run "sudo nvidia-xconfig". Once i ran that and rebooted the system told me there there was no device! Still no drivers in the hardware drivers section...

if it helps im using nvidia-glx-173 from synaptic.

---

### Post by iman1000000 on 2009-02-14
Success! After a python update Envyng could install the correct drivers properly. Still doesn't turn up in the hardware drivers though...;)

---

