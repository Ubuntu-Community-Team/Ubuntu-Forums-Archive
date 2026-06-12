---
title: "Nvidia drivers failing."
date: 2010-04-30
forum: Desktop Environments
---

### Post by rslink on 2010-04-30
I installed 10.4,every thing was fine, installed updates, restarted it goes to a black screen. Selecting the second Ubuntu on the list in grub allows me to start Ubuntu. While it does the screen flashes etc, failed to load x, run Ubuntu in low graphics it starts normally.  I installed the latest driver from Nvidia, x is set to use that driver. In some other things I have tried it fails to load the Nvidia kernel.  Nvidia  geforce 9800 GT and a Nvidia nforce 780a onboard.  Any ideas?

---

### Post by telescopic on 2010-05-11
I don't know if i have the same problem as yours. I was using Xubuntu 9.10 with default video driver; I try to install Nivdia proprietary driver from Hardware upgrade, but i canceled the installation in the mid-course. After reboot, I have grub list, choose xubuntu, then get black screen. It does not work anymore.

---

### Post by razy60 on 2010-05-11
hi, try on start up hitting either escape or hold down shift i think it is, this should give you a choice of kernels choose the one ending .21,
it seems the .22 kernel is unhappy with the nvidia drivers.

Raz

---

