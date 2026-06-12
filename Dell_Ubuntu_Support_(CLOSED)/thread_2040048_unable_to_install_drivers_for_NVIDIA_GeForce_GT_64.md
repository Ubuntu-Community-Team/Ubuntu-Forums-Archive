---
title: "unable to install drivers for NVIDIA GeForce GT 640M in ubuntu 12.04 64 bit"
date: 2012-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanatkrtiwari86 on 2012-08-10
Recently I purchased Dell inspiron 7420 with NVIDIA GeForce GT 640M DDR3 2GB graphic card. Ubuntu 12.04 64 bit installed and working fine with its integrated intel graphic card driver.
I tried hard to install nvidia drivers in my machine but failed always.
I checked for such questions in forums and did all they suggested but still in trouble. The things i did are as follows:

1. installed nvidia-current drivers. but it crashed my glxgears etc. Also once I run nvidia-xconf in root and reboot.
The xorg.conf freeze with 640x480 (something like that) resolution and no way i could change it. 

2. Then i installed bumblebee and bumblebee-nvidia. Followed related instructions. But no success. 

Can anyone please tell me the proper procedure to get it installed from scratch.

I followed a similar post in this section with removing all nvidia with purge command and removing xorg.conf. then

```
sudo add-apt-repository ppa:bumblebee/stable 
sudo apt-get update 
sudo apt-get install bumblebee bumblebee-nvidia
```

and then 
```
sudo apt-get install --reinstall nvidia-current
```

but after reboot, when i try
```
optirun glxspheres
```
The output is 
```
[   53.354577] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0

[   53.354606] [ERROR]Aborting because fallback start is disabled.

```

---

### Post by sanatkrtiwari86 on 2012-08-12
bump
please help

---

