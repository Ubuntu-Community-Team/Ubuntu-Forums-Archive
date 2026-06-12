---
title: "Intel linux drivers?"
date: 2009-04-09
forum: General Help
---

### Post by wolfyking2 on 2009-04-09
Are there any linux intel drivers?  Because my graphics suck and wanted to now if I could give it a little boost ;)

---

### Post by 3rdalbum on 2009-04-09
There are Intel drivers; these should be loaded automatically for you. What chipset do you have? Please post the output of this command:

```
lspci
```

Maybe the driver is already loaded?

```
glxinfo | grep "direct"
```

If you get "direct rendering: Yes" then the driver is working.

Intel chipsets aren't very good for graphics; I'd recommend Nvidia.

---

### Post by skymera on 2009-04-09
Intel chips are weak, and the "Intel" driver is the best as it gets really.

Pick up a cheap Nvidia, they work relatively well and will have much more oomph than your Intel chip

---

### Post by LowSky on 2009-04-09
> **skymera said:**
> Intel chips are weak, and the "Intel" driver is the best as it gets really.

Pick up a cheap Nvidia, they work relatively well and will have much more oomph than your Intel chip

you cant pick up a graphics card if they are using a laptop.
Just wanted to put that info out there

It is possible his PC is using the wrong intel driver, and some intel chip run really bad regardless, follow 3rdalbum commands and let us know the hardware your using.

thanks

---

