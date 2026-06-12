---
title: "Linux steam performance"
date: 2016-06-25
forum: Gaming &amp; Leisure
---

### Post by Omar_Jair on 2016-06-25
Ill start this straight, since i migrated to Ubuntu i haven't used it for gaming, but now i noticed something a bit off, I thought that, since my desktop is a lot lighter than Unity or GNOME i would not have any issues while gaming some low spec games like Half Life 2 or so, but it seems that even those lag now on Ubuntu MATE, is there a way to increase performance so they run smoothly again? i dont wanna have a windows machine just for gaming.

---

### Post by oldrocker99 on 2016-06-25
What are your machine's specs? CPU, GPU, RAM, open source or proprietary drivers? I use Ubuntu MATE myself.

---

### Post by Omar_Jair on 2016-06-26
Here are my specs.
```
omar@Ubuntuforums:~$ inxi -FxzSystem:    Host: Ubuntuforums Kernel: 4.4.0-24-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3)
           Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA product: Satellite C55-B v: PSCMLU-08D0EJ
           Mobo: TOSHIBA model: ZBWAA v: 1.00
           Bios: TOSHIBA v: 1.70 date: 12/11/2014
CPU:       Dual core Intel Celeron N2840 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8652
           clock speeds: max: 2582 MHz 1: 2182 MHz 2: 2004 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-24-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (6.1% used)
           ID-1: /dev/sda model: HGST_HTS545050A7 size: 500.1GB
Partition: ID-1: / size: 455G used: 25G (6%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 4.18GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 195 Uptime: 4 min Memory: 912.1/3839.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.35
```

---

### Post by oldrocker99 on 2016-06-27
It would appear that your machine, with an Atom processor and Intel graphics, simply doesn't have the horsepower to run very graphically-intensive games. That doesn't mean that all games are unplayable; you just have to try each one and hope for the best. If Half-Life 2 won't run well, try Half-Life. Older games (the Half-Life series, Baldurs Gate and the other Infiinity Engine games, and most newer minimal-graphics indie games) usually run pretty well. I know that the Orange Box games aren't exactly new, but they might just be too heavy on the graphics requirements.

I hope this "bad" news doesn't discourage you too much.

---

### Post by Omar_Jair on 2016-06-27
Nah, i meant that those low spec games were running fine, idk why Ubuntu Steam cant lift up too much fps as windows did, xD af for the computer well, i always knew intel was crappy, is there a way to improve steam a bit here?

---

### Post by X-RED_Tech on 2016-06-27
Nothing to improve, I'm afraid. 

In Windows those games you were used to were probably running the native and proprietary DirectX whereas in Ubuntu (or Mac) they'll have to make do with OpenGL.

---

