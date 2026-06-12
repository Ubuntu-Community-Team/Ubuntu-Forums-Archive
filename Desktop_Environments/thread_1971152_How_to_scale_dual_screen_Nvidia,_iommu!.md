---
title: "How to scale dual screen? Nvidia, iommu!"
date: 2012-05-02
forum: Desktop Environments
---

### Post by turbos4 on 2012-05-02
Hello

I'm trying to dual screen with diffrent font og scale.

First I use nouveau open source driver for my NVIDIA.

Can't install nvidia-current, nvidia-current-updates or the driver provided from NVIDIA.
Because of i need IOMMU and amd-v I get this error:

[B][SIZE=2][   49.895890] NVRM: RmInitAdapter failed! (0x27:0x38:1190)
 [   49.895898] NVRM: rm_init_adapter(0) failed
 [   50.087448] init: lightdm main process (1400) terminated with status 1
 [   65.113865] init: failsafe-x main process (1796) terminated with status 1[/SIZE][/B]

Ubuntu desktop won't start when using NVIDIA driver.



#lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560] (rev a1)


I won't to diffrent scale on screens. How can i do that?


Have to screens acer 22" (AL2251W) 1680x1050_60 and samsung 50" 1920x1080_60.


Everything i tried just do on both screen at the same time.

---

### Post by turbos4 on 2012-05-02
Have a fresh install of Ubuntu 12.04 LTS.

#uname -a
Linux server1 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mips on 2012-05-02
I always install my nvidia drivers from the x-swat PPA.

I'm also running dual screens at 1680x1050 & 1920x1080 but under Xubuntu.

---

### Post by turbos4 on 2012-05-14
Prøvde x-swat PPA, men samme feilen der. IOMMU fungerer ikke på NVIDIA.

---

