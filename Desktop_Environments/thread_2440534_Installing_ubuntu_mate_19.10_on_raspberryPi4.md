---
title: "Installing ubuntu mate 19.10 on raspberryPi4"
date: 2020-04-12
forum: Desktop Environments
---

### Post by sgy939 on 2020-04-12
I currently have Xubuntu running on a raspberry Pi4
Previous post
[https://ubuntuforums.org/showthread.php?t=2438433&p=13946097#post13946097](https://ubuntuforums.org/showthread.php?t=2438433&p=13946097#post13946097)


```

ubuntu@ubuntu:~$ inxi -Fxz
System:
  Host: ubuntu Kernel: 5.3.0-1018-raspi2 armv7l bits: 32 compiler: gcc 
  v: 9.2.1 Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: ARM Device System: Raspberry Pi 4 Model B Rev 1.2 details: BCM2835 
  rev: c03112 serial: <filter> 
Argument "Raspberry Pi 4 Model B Rev 1.2" isn't numeric in sprintf at /usr/bin/inxi line 6997.
CPU:
  Topology: Quad Core model: ARMv7 v7l variant: cortex-a72 bits: 32 
  type: MCP arch: v7l rev: 3 
  features: Use -f option to see features bogomips: 432 
  Speed: 600 MHz min/max: 600/1500 MHz Core speeds (MHz): 1: 600 2: 600 
  3: 600 4: 600 
Graphics:
  Device-1: bcm2708-fb driver: bcm2708_fb v: kernel bus ID: N/A 
  Device-2: bcm2835-hdmi driver: N/A bus ID: N/A 
  Display: x11 server: X.Org 1.20.5 driver: fbdev unloaded: modesetting 
  resolution: 1280x1024~N/A 
  OpenGL: renderer: llvmpipe (LLVM 9.0 128 bits) v: 3.3 Mesa 19.2.8 
  direct render: Yes 
Audio:
  Device-1: bcm2835-hdmi driver: N/A bus ID: N/A 
Network:
  Message: No ARM data found for this feature. 
  IF-ID-1: eth0 state: down mac: <filter> 
  IF-ID-2: wlan0 state: up mac: <filter> 
Drives:
  Local Storage: total: 29.81 GiB used: 5.08 GiB (17.0%) 
  ID-1: /dev/mmcblk0 model: EB1QT size: 29.81 GiB 
Partition:
  ID-1: / size: 29.05 GiB used: 4.98 GiB (17.2%) fs: ext4 
  dev: /dev/mmcblk0p2 
Sensors:
  Message: No sensors data was found. Is sensors configured? 
Info:
  Processes: 218 Uptime: 13m Memory: 3.73 GiB used: 646.6 MiB (16.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.2.1 Shell: bash v: 5.0.3 
  inxi: 3.0.36 
ubuntu@ubuntu:~$ 

```

I'd like to install Mate 19.10
I found the following code

```
sudo apt update && sudo apt upgrade -y
sudo apt install ubuntu-mate-desktop
```

on   [https://itsfoss.com/install-mate-desktop-ubuntu/](https://itsfoss.com/install-mate-desktop-ubuntu/)
It is for    Ubuntu 18.04 and other versions
Will the above code work for Mate 19.10?    If not, what is the correct way to do so?

Thanks

---

### Post by mikewhatever on 2020-04-12
It should work on all supported releases.

---

### Post by sgy939 on 2020-04-15
thanks for your reply!
it worked

---

