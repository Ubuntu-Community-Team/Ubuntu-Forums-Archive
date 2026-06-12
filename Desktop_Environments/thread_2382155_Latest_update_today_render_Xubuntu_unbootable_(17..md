---
title: "Latest update today render Xubuntu unbootable (17.10)"
date: 2018-01-09
forum: Desktop Environments
---

### Post by mrouilla515 on 2018-01-09
The latest update today has render Xubuntu 17.10 unbootable. The boot process is stuck at a blinking cursor. I tried a previous kernel but same result. Calling a terminal does not work either. I don't know if it is related with the latest woos with 17.10 or the publicized Intel fiasco but what ever that update was, it is a desaster. I have a triple boot system (Mint 18.3, Xubuntu 17.10 and Windows 7. Beside Xubuntu, the others are not affected. Any idea on how to recover from this ???

Amd FX6300
Nvidia 650GT-TI
Amd motherboard Gigabyte Ga-970A-D3

---

### Post by mrouilla515 on 2018-01-09
Ok got it going again. I did a grub update in Mint (grub-customizer) and that unlock Xubuntu. My explanation (?) ; There was a kernel update (4.13.0.25) in that last update and because Mint seems to own the loader, Xubuntu could not update it. Updating grub in Mint reestablish the correct boot entry for Xubuntu. Still that's the first time I see this.

Fiouf saved, this time.

---

