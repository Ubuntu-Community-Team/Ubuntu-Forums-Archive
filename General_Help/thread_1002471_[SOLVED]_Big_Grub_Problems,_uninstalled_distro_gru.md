---
title: "[SOLVED] Big Grub Problems, uninstalled distro grub was installed on."
date: 2008-12-05
forum: General Help
---

### Post by lszanto on 2008-12-05
I recently installed kubuntu on my machine aswell as ubuntu, but as I was not fond of it I removed it after a few days. Upon doing this grub went all haywire and when it started it shows starting stage 1.5 and then has error 17? I think. I have tried all the grub-install /dev/sda1 and the grub terminal setup and root stuff but nothing works. I am most likley going to just reinstall ubuntu unless I can get a solution, any suggestions?

thanks, Luke

---

### Post by Nathan Sweeney on 2008-12-05
> **lszanto said:**
> I recently installed kubuntu on my machine aswell as ubuntu, but as I was not fond of it I removed it after a few days. Upon doing this grub went all haywire and when it started it shows starting stage 1.5 and then has error 17? I think. I have tried all the grub-install /dev/sda1 and the grub terminal setup and root stuff but nothing works. I am most likley going to just reinstall ubuntu unless I can get a solution, any suggestions?

thanks, Luke

Grub is probably having issues because it looks for a file /boot/grub/menu.lst.  If you installed grub from kubuntu and then deleted kubuntu, it can no longer find the menu.lst file it needs.

Why are you trying to install grub to /dev/sda1 instead of the MBR?

---

### Post by lszanto on 2008-12-06
Um to be honest I don't really mind where it is installed to, I just want it to work, the kubuntu will have installed it to the default place that kubuntu installs grub to, I'm not sure if that is MBR or just to a partiton. Is there a way to check or reset my MBR so I can reinstall grub?

---

### Post by caljohnsmith on 2008-12-07
> **lszanto said:**
> Um to be honest I don't really mind where it is installed to, I just want it to work, the kubuntu will have installed it to the default place that kubuntu installs grub to, I'm not sure if that is MBR or just to a partiton. Is there a way to check or reset my MBR so I can reinstall grub?
If you deleted Kubuntu, what OSes are left on the HDD? If you only have Windows left on the drive, you could install a Windows MBR (Master Boot Record) so that you boot straight into Windows. Or if you have another Linux distro on the HDD, you can reinstall Grub to the MBR and let the other distro take control of the booting process. If you want to reinstall a Windows MBR, just boot your Windows XP Install CD, go to the "recovery console" and run:
```
fixmbr
```
Or if you have another Linux distro you want to take control of Grub in the MBR, how about first posting:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

