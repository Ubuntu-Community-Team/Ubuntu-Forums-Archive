---
title: "Cinnamon desktop runs only in software rendering mode."
date: 2020-04-15
forum: Desktop Environments
---

### Post by sgy939 on 2020-04-15
Ubuntu desktops on raspberry pi 4
Previous posts
[https://ubuntuforums.org/showthread.php?t=2438433&p=13946097#post13946097](https://ubuntuforums.org/showthread.php?t=2438433&p=13946097#post13946097)
[https://ubuntuforums.org/showthread.php?t=2440534&p=13946946#post13946946](https://ubuntuforums.org/showthread.php?t=2440534&p=13946946#post13946946)

Downloaded and flashed, Ubuntu Server 19.10.1 , to a 32GB SD card. Installed xubuntu desktop.
Cloned that to a couple of other sd cards.
Installed Ubuntu Mate on one.
[https://itsfoss.com/install-mate-desktop-ubuntu/](https://itsfoss.com/install-mate-desktop-ubuntu/)
Runs with no problems.
Installed cinnamon desktop from
[https://www.tecmint.com/install-cinnamon-desktop-on-ubuntu/](https://www.tecmint.com/install-cinnamon-desktop-on-ubuntu/)
using the Universe PPA
Rebooted after install. Selected cinnamon at login.
I get a warning that cinnamon is running in software rendering mode.
Log out and select Xfce session there are no problems.
The GPU settings are the same in both desktops
The only difference are the desktops.

[HTML]ubuntu@ubuntu:~$ inxi -xx-S
System:
  Host: ubuntu Kernel: 5.3.0-1022-raspi2 armv7l bits: 32 compiler: gcc 
  v: 9.2.1 Desktop: Gnome 3.34.1 wm: xfwm4 dm: LightDM 
  Distro: Ubuntu 19.10 (Eoan Ermine) 
ubuntu@ubuntu:~$ inxi -xx-G
Graphics:
  Device-1: bcm2708-fb driver: bcm2708_fb v: kernel bus ID: N/A 
  chip ID: brcm:soc 
  Device-2: bcm2835-hdmi driver: N/A bus ID: N/A chip ID: brcm:soc 
  Display: x11 server: X.Org 1.20.5 driver: fbdev unloaded: modesetting 
  resolution: 1280x1024~N/A 
  OpenGL: renderer: llvmpipe (LLVM 9.0 128 bits) v: 3.3 Mesa 19.2.8 
  compat-v: 3.1 direct render: Yes 
ubuntu@ubuntu:~$ 
[/HTML]


[HTML]ubuntu@ubuntu:~$ inxi -xx-S
System:
  Host: ubuntu Kernel: 5.3.0-1022-raspi2 armv7l bits: 32 compiler: gcc 
  v: 9.2.1 Desktop: Cinnamon 4.0.10 dm: LightDM 
  Distro: Ubuntu 19.10 (Eoan Ermine) 
ubuntu@ubuntu:~$ inxi -xx-G
Graphics:
  Device-1: bcm2708-fb driver: bcm2708_fb v: kernel bus ID: N/A 
  chip ID: brcm:soc 
  Device-2: bcm2835-hdmi driver: N/A bus ID: N/A chip ID: brcm:soc 
  Display: x11 server: X.Org 1.20.5 driver: fbdev unloaded: modesetting 
  resolution: 1280x1024~N/A 
  OpenGL: renderer: llvmpipe (LLVM 9.0 128 bits) v: 3.3 Mesa 19.2.8 
  compat-v: 3.1 direct render: Yes 
ubuntu@ubuntu:~$ 
[/HTML]

Is there a way to get the cinnamon desktop not to run in software rendering mode?

In case you are wondering why I'm doing this project?   A lot of time on my hands  during this Covid-19 lock down.  It helps to keep my mind occupied,  (maybe keep my sanity),    with something not related to it. 

Thanks for your replies in advance!

---

