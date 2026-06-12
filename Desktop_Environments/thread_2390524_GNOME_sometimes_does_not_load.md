---
title: "GNOME sometimes does not load"
date: 2018-04-29
forum: Desktop Environments
---

### Post by Odisej on 2018-04-29
Dear all,

I am experiencing a small problem with the latest Ubuntu Bionic. Gnome sometimes doesn't load. After GDM I only get purple screen. I need your help.

1. I need to access a log that would show me what is happening. Which file should I check?

2. Where can I access reported bugs for Ubuntu and see if I can find a solution there?

If you have some additional ideas I am posting my hardware info bellow:

```

System:    Host: bigbox Kernel: 4.15.0-20-generic x86_64 bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: H110M-D v: Rev X.0x serial: N/A
           UEFI: American Megatrends v: 3016 date: 12/27/2016
CPU:       Quad core Intel Core i5-7600 (-MCP-) cache: 6144 KB
           clock speeds: max: 4100 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz
Graphics:  Card: NVIDIA GP107 [GeForce GTX 1050 Ti]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 1050 Ti/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.48
Audio:     Card-1 NVIDIA GP107GL High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 Intel Sunrise Point-H HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp3s0 state: up speed: 100 Mbps duplex: full
           mac: 70:4d:7b:68:4d:7b
Drives:    HDD Total Size: 740.2GB (77.5% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 240.1GB
           ID-2: /dev/sdb model: WDC_WD5000AADS size: 500.1GB
Partition: ID-1: / size: 49G used: 5.6G (12%) fs: ext4 dev: /dev/sda3
           ID-2: /boot size: 976M used: 84M (10%) fs: ext4 dev: /dev/sda2
           ID-3: /home size: 162G used: 121G (79%) fs: ext4 dev: /dev/sda5
           ID-4: swap-1 size: 8.45GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 37C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 270 Uptime: 16 min Memory: 2409.5/15984.4MB
           Client: Shell (bash) inxi: 2.3.56 


```

---

### Post by Xian on 2018-04-29
> **Odisej said:**
> 
I am experiencing a small problem with the latest Ubuntu Bionic. Gnome sometimes doesn't load. After GDM I only get purple screen. I need your help.

1. I need to access a log that would show me what is happening. Which file should I check?


What is the output of this command:

```
[COLOR=#141414][FONT=monospace]cat /var/log/Xorg.0.log | egrep "EE|WW"[/FONT][/COLOR]
```

---

### Post by Xian on 2018-04-29
If that doesn't reveal anything remarkable check this file's content in your $HOME directory.

~.xsession-errors

---

### Post by Odisej on 2018-05-04
Xian, thanks for suggestions. 

Well, i opted for xubuntu for now. There were too many crashes and problems with Gnome (couldn't switch users properly and such).

I also waited for Gnome not to load again. It happened once but I could not find anything in the suggested logs.

Will probably return to Gnome in while although I am really enjoying xfce currently. No problems or crashes so far. 

Btw, I have Ubuntu on several computers and only on one machine the loading problem occurs. Go figure.

Regards,

Odisej

---

