---
title: "Nvidia GF 6800GS wont install"
date: 2006-03-03
forum: Desktop Environments
---

### Post by Ozxobez on 2006-03-03
Today i tried to install Ubuntu on my machine. It all went well until i tried to install my Nvidia drivers. The drivers install succesfully (used method 1 and 2 in the Nvidia driver howto thread on these forums) but when i reboot i get a black screen. Spec's:

AMD Athlon64 3500+
1gb DDR PC3200
160GB SATA2
EVGA Nvidia Geforce 6800GS CO (overclocked version)

The pc is connected to a Acer AL1751 monitor (trough DVI). I also tried to install suse 10, i followed the directions on the nvidia site for SuSe. Same story, also a black screen.

Once i change the "nvidia" back to "nv" (in safe mode) it says something with a "HAL" error. Any help would be appriciated. :)

---

### Post by Ozxobez on 2006-03-03
I found the "bug" :) after installing the drivers, the card starts using the first monitor connector on the GFX card. My GFX card has two connectors:

1. sub-d (a normal VGA connector)
2. DVI

I plugged my monitor onto the DVI connector. When i plug it onto the sub-d connector and reboot, everything works ok. Now is my question, how to i get the DVI connector working?

Thanks in advance.

---

### Post by Ozxobez on 2006-03-03
Found the solution :)

add to the xorg.conf this: Option "ConnectedMonitor" "DFP"

---

