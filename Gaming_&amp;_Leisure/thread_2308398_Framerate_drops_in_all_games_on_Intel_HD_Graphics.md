---
title: "Framerate drops in all games on Intel HD Graphics"
date: 2016-01-02
forum: Gaming &amp; Leisure
---

### Post by mrzapp2 on 2016-01-02
Hi,

I am experiencing serious framerate drops (down to around 2-4fps) in all games on my **Thinkpad T420** with **Intel HD Graphics 3000**.
The games I've tried have been both very high and very low demand games on both ultra high and ultra low settings, the results are the same.

I am told that there is **no need to install proprietary drivers** for the Intel cards, as they are included in the kernel, which I would love to believe, but it really seems to be a driver issue.
The problems occur with native drivers both on **Ubuntu 14.04.3** and on **Ubuntu 15.10** in both **awesome wm** and **Gnome 3**.

I have tried a few things:

1. **intel-linux-graphics-installer** (couldn't install)
This GUI installer can be downloaded from here: [https://01.org/linuxgraphics/downloads/](https://01.org/linuxgraphics/downloads/)
They only support the latest unstable Ubuntu, and all links to previous versions are broken.
I managed to fetch a copy of the 1.0.7 version, which was supposed to support Ubuntu 14.04.3, but still rejected my distro during the install.

2. **xorg-xserver-video-intel** (breaks the system beyond my ability to repair)
I got recommended the above mentioned package, but as soon as I installed it and rebooted, gdm wouldn't start, and switching to tty in order to uninstall the package didn't solve it either.
I had to reinstall the system to get it back.

Does anyone here have a similar experience with this card or machine?
Thanks in advance!

**Output of inxi -Fxz**:
```

System:    Host: tor Kernel: 3.19.0-42-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Awesome 3.4.15 Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO product: 4180AV8 version: ThinkPad T420
           Mobo: LENOVO model: 4180AV8 Bios: LENOVO version: 83ET66WW (1.36 ) date: 10/31/2011
CPU:       Dual core Intel Core i5-2520M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9967.86 
           Clock Speeds: 1: 800.00 MHz 2: 799.902 MHz 3: 800.00 MHz 4: 800.00 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.17.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1600x900@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 10.5.9 Direct Rendering: Yes
Audio:     Card: Intel 6 Series/C200 Series Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-42-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e ver: 2.3.2-k port: 5080 bus-ID: 00:19.0
           IF: eth0 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi ver: in-tree: bus-ID: 03:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 160.0GB (15.7% used) 1: id: /dev/sda model: INTEL_SSDSA2BW16 size: 160.0GB 
Partition: ID: / size: 47G used: 5.1G (12%) fs: ext4 ID: /home size: 92G used: 19G (22%) fs: ext4 
           ID: swap-1 size: 8.47GB used: 0.02GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 51.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: 3589 
Info:      Processes: 188 Uptime: 2 days Memory: 1431.0/7867.0MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 


```

---

### Post by deadflowr on 2016-01-02
I've moved this thread to **Gaming and Leisure**, 
as users who frequent here will be more adept at figuring out what's going on.

---

### Post by mrzapp2 on 2016-01-02
Duh, of course. Thanks a bunch :)

---

### Post by peter226 on 2016-01-05
I would like to bump this thread, because I am seeing the exact same problems as described. 
I am also using a Sandy Bridge mobile processor.

All applications that make intensive use of OpenGL run at full framerate for about 10 seconds or so, then plummet to nearly half.

I have spent the past week trying to identify the problem to know avail. Help from anybody is appreciated. Thank you!

---

### Post by mastablasta on 2016-01-06
intel drivers are included in the kernel.

you can upgrade them using xorg edgers PPA : [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)
or oibaf: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

make sure you read instructions well. particulary the part on how to restore the OS to previous state as well as what kind of changes are made. and bear in mind these are beta versions.

---

