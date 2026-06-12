---
title: "Wine Crash on Optimus using Nvidia"
date: 2016-02-23
forum: Gaming &amp; Leisure
---

### Post by Berwyn_Powell on 2016-02-23
Hello There,

I was hoping one of the good people on the forums would be able to help me. I've recently moved back to Ubuntu from Fedora due to better Optimus support (I could only use Bumblebee on Fedora and it wouldn't recompile with a kernel update) and have run into a little issue when setting up wine. I've got a few games installed, and all run fine when using the Intel Card on my Optimus Laptop (ASUS N550JV), but any d3d games crash when I try running them through the nVidia card with the following error:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  21 (RRSetCrtcConfig)
  Value in failed request:  0x0
  Serial number of failed request:  931
  Current serial number in output stream:  931
0
If anyone has any ideas how to fix this it would be greatly appreciated. Native OpenGL games run absolutely fine, as do any 2d games on the nVidia Card (Starcraft, AoE2 etc.) I'm using Ubunutu MATE 15.10, Wine from the Official Repo's, and the nVidia 361.28 driver from ppa:graphics-drivers/ppa

Thanks, Bez

P.S. My apologies if this has been asked before, but I did a search and couldn't find anything related.

---

### Post by Bucky Ball on 2016-02-23
You don't mention which NVidia GPU you are using nor the model of the Intel internal card. That driver will cause issues with some NVidia GPUs. Have you tried the one in Additional Drivers, 352.** from memory? Which driver is recommended for your card there?

---

### Post by Berwyn_Powell on 2016-02-23
> **Bucky Ball said:**
> You don't mention which NVidia GPU you are using nor the model of the Intel internal card. That driver will cause issues with some NVidia GPUs. Have you tried the one in Additional Drivers, 352.** from memory? Which driver is recommended for your card there?

Sorry, that was an oversight on my part. the nVidia card is a GT 750m and the Intel is a Haswell i7 (not sure of exact model). I'll give the older drivers a go and report back.

---

### Post by Berwyn_Powell on 2016-02-23
Just tried the 352 drivers and I've got exactly the same result (with a slightly different serial number obviously). I don't remember any of the drivers being marked as recommended in additional drivers, but obviously the one from the official Ubuntu repo's has the same issue. Is it possible I'm missing a 32-bit library from the nVidia drivers that's present in the Intel ones?

---

