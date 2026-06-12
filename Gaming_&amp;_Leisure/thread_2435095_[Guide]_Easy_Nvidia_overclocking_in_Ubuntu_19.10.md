---
title: "[Guide] Easy Nvidia overclocking in Ubuntu 19.10"
date: 2020-01-16
forum: Gaming &amp; Leisure
---

### Post by sebastian1978 on 2020-01-16
Hello,

Here is my way of overclocking Nvidia in Ubuntu 19.10

Only 4 easy steps:
1. I installed latest proprietary Nvidia drivers.
2. I added and set option Coolbits to 29 in /usr/share/X11/xorg.conf.d/10-nvidia.conf:
```
sudo gedit /usr/share/X11/xorg.conf.d/10-nvidia.conf

```
 
```
Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
Option "Coolbits" "29"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia-430/xorg"
EndSection
``` 

You can choose needed value of Coolbits based on [https://bitcointalk.org/index.php?topic=2848723.0](https://bitcointalk.org/index.php?topic=2848723.0)
Note: I didn't use xorg.conf for adding Coolbits because *xorg.conf being overwritten*
3. Installed GreenWithEnvy (GWE)
See [https://www.omgubuntu.co.uk/2019/02/easily-overclock-nvidia-gpu-on-linux-with-this-new-app](https://www.omgubuntu.co.uk/2019/02/easily-overclock-nvidia-gpu-on-linux-with-this-new-app) for installation instructions
4. Set overclocking parameters in GWE


Enjoy! Hope somebody will find my experience useful.

---

