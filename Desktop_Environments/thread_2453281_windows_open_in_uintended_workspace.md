---
title: "windows open in uintended workspace"
date: 2020-11-06
forum: Desktop Environments
---

### Post by Skaperen on 2020-11-06
i start an application that takes a few seconds to open its window(s).  that may be because it is bulky and has to load tons of libraries nothing else uses.  or it could be started with a delay for some reason like network activity.  while that is taking place, i switch over to a different workspace to do something else for a minute.  that application opens its window(s) in the workspace i switched to.  what's up with that?

---

### Post by yapidumoac on 2020-11-06
What is the name of this application. You could also post details of you system. From the command line, run &#8216;inxi -F&#8217; and post the results to [https://pastebin.com/](https://pastebin.com/) If inxi isn't installed then you can install it using &#8216;sudo apt-get install inxi&#8217;

---

### Post by Skaperen on 2020-11-06
every application that opens windows in X is affected.

Xubuntu 18.04.5 last upgraded yesterday
```

System:    Host: lt2a Kernel: 5.4.0-52-generic x86_64 bits: 64 Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.5 LTS
Machine:   Device: laptop System: System76 product: Kudu Professional v: kudp1b serial: N/A
           Mobo: System76 model: Kudu Professional v: kudp1b serial: N/A
           BIOS: American Megatrends v: 1.03.05RS762 date: 06/23/2014
Battery    BAT0: charge: 58.0 Wh 100.0% condition: 58.0/62.2 Wh (93%)
CPU:       Quad core Intel Core i7-4710MQ (-MT-MCP-) cache: 6144 KB
           clock speeds: max: 3500 MHz 1: 1136 MHz 2: 1783 MHz 3: 1350 MHz 4: 1313 MHz 5: 1472 MHz 6: 1229 MHz
           7: 1431 MHz 8: 1321 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller
           Display Server: x11 (X.Org 1.20.8 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) version: 4.5 Mesa 20.0.8
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k5.4.0-52-generic
Network:   Card-1: Intel Wireless 7260 driver: iwlwifi
           IF: wlp4s0 state: up mac: f8:16:54:2c:d7:06
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp5s0f2 state: down mac: 80:fa:5b:06:24:5f
Drives:    HDD Total Size: 2120.4GB (31.7% used)
           ID-1: /dev/sda model: HGST_HTS721010A9 size: 1000.2GB
           ID-2: /dev/sdb model: Samsung_SSD_840 size: 120.0GB
           ID-3: /dev/sdc model: HGST_HTS721010A9 size: 1000.2GB
Partition: ID-1: / size: 16G used: 12G (78%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 886G used: 599G (72%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 17.18GB used: 0.24GB (1%) fs: swap dev: /dev/sdc2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 1388 Uptime: 1 day Memory: 10385.3/15933.3MB Client: Shell (bash) inxi: 2.3.56 

```

---

### Post by ActionParsnip on 2020-11-08
Is it an application installed using snap? If so, this is normal

---

### Post by vanadium on 2020-11-08
I am afraid this is normal behavior. Once the application is ready, the window will be created on the current workspace. In this context, the default behavior of Gnome Shell would suit you better: there, that window is not focussed. You get a notication "that it is ready". Still, it will be created on the current workspace.

---

### Post by Skaperen on 2020-11-09
so what can i do to have the window created in workspace 4?

---

