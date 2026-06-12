---
title: "Ubuntu 18.04 - Double icons on the dash and on the panel"
date: 2020-04-04
forum: Desktop Environments
---

### Post by Apanta on 2020-04-04
Hello.
Yesterday I updated the s.o. to the 5.3.0-45 kernel. Restarted and worked for at least 3 hours, all ok.
This morning, starting the PC I saw that on the side dash and on the upper panel the icons are all double.
These are the data of my Ubuntu:
[PHP]apanta@apanta-desktop:~$ inxi -Fzr
System:    Host: apanta-desktop Kernel: 5.3.0-45-generic x86_64 bits: 64
           Desktop: Gnome 3.28.4 Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop Mobo: ASRock model: K10N78FullHD-hSLI.. serial: N/A
           BIOS: American Megatrends v: P2.30 date: 04/30/2010
CPU:       Dual core AMD Athlon 64 X2 5200+ (-MCP-) cache: 1024 KB
           clock speeds: max: 2700 MHz 1: 2400 MHz 2: 2400 MHz
Graphics:  Card-1: NVIDIA C77 [GeForce 8200]
           Card-2: NVIDIA GF106 [GeForce GTS 450]
           Display Server: x11 (X.Org 1.20.5 ) driver: nvidia
           Resolution: 1280x1024@60.02hz, 1280x1024@60.02hz
           OpenGL: renderer: GeForce GTS 450/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.116
Audio:     Card-1 NVIDIA GF106 High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 TerraTec Electronic Aureon Dual USB driver: USB Audio
           Card-3 Logitech Webcam C310 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k5.3.0-45-generic
Network:   Card-1: NVIDIA MCP77 Ethernet driver: forcedeth
           IF: enp0s10 state: down mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 3500.7GB (22.6% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 500.1GB
           ID-2: /dev/sdb model: ST2000DM001 size: 2000.4GB
           ID-3: /dev/sdc model: ST31000528AS size: 1000.2GB
Partition: ID-1: / size: 49G used: 11G (23%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 8.00GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.0C mobo: N/A gpu: 37C
           Fan Speeds (in rpm): cpu: N/A
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://it.archive.ubuntu.com/ubuntu/ bionic main restricted
           deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
           deb http://it.archive.ubuntu.com/ubuntu/ bionic universe
           deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates universe
           deb http://it.archive.ubuntu.com/ubuntu/ bionic multiverse
           deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
           deb http://it.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
           deb http://archive.canonical.com/ubuntu bionic partner
           deb http://security.ubuntu.com/ubuntu bionic-security main restricted
           deb http://security.ubuntu.com/ubuntu bionic-security universe
           deb http://security.ubuntu.com/ubuntu bionic-security multiverse
           Active apt sources in file: /etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-bionic.list
           deb http://ppa.launchpad.net/gerardpuig/ppa/ubuntu bionic main
           Active apt sources in file: /etc/apt/sources.list.d/pj-assis-ubuntu-ppa-bionic.list
           deb http://ppa.launchpad.net/pj-assis/ppa/ubuntu bionic main
           Active apt sources in file: /etc/apt/sources.list.d/skype-stable.list
           deb [arch=amd64] https://repo.skype.com/deb stable main
Info:      Processes: 205 Uptime: 17 min Memory: 1446.2/7457.4MB
           Client: Shell (bash) inxi: 2.3.56 
apanta@apanta-desktop:~$  [/PHP]

 noticed that the icons that I had added to favorites or that were present by default are "clickable and operational", while the other icons that have appeared now are not accessible.
This is very annoying.
[ATTACH=CONFIG]285393[/ATTACH]
[ATTACH=CONFIG]285394[/ATTACH]
I read a discussion a few years ago where it was written that it could be a cache and history problem to be deleted, but I would not know where to look if not here:

[ATTACH=CONFIG]285396[/ATTACH]
 Tried booting with the 5.3.0-42 kernel, but the problem persists.
I also saw inside usr/share/applications, but the icons into the folder are single and not duplicated.
Please I need your help to solve, thanks

---

### Post by Apanta on 2020-04-05
Ok   solved it by uninstalling dconf-editor

---

