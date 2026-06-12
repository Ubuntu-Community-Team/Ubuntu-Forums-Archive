---
title: "HDMI stopped working after last week`s upgrade"
date: 2023-07-24
forum: Desktop Environments
---

### Post by andrec137 on 2023-07-24
Recently bought a new HDMI cable, worked fine in two different monitors. After a recent upgrade (I do not know if it was for the entire xubuntu or just other things, I was prompted to update and said yes) it stopped working. I do not know if the upgrade was the thing that made it stop working, it is the only thing I can think of.

This is my inxi -Fxxxrz results:
```
System:
  Kernel: 5.19.0-46-generic x86_64 bits: 64 compiler: N/A
    Desktop: Xfce 4.16.0 tk: Gtk 3.24.23 info: xfce4-panel wm: xfwm 4.16.1
    vt: 7 dm: LightDM 1.30.0 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Dell product: Inspiron 15 7000 Gaming v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: Dell model: 0TXG2N v: X02 serial: <superuser required> UEFI: Dell
    v: 1.7.0 date: 05/08/2018
Battery:
  ID-1: BAT0 charge: 1.1 Wh (100.0%) condition: 1.1/74.0 Wh (1.5%)
    volts: 12.2 min: 11.1 model: Samsung SDI DELL 0GFJ671 type: Li-ion
    serial: <filter> status: Full
CPU:
  Info: quad core model: Intel Core i5-7300HQ bits: 64 type: MCP
    smt: <unsupported> arch: Kaby Lake rev: 9 cache: L1: 256 KiB L2: 1024 KiB
    L3: 6 MiB
  Speed (MHz): avg: 3199 high: 3299 min/max: 800/3500 cores: 1: 3298
    2: 3100 3: 3100 4: 3299 bogomips: 19999
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel HD Graphics 630 vendor: Dell driver: i915 v: kernel ports:
    active: eDP-1 empty: DP-1 bus-ID: 00:02.0 chip-ID: 8086:591b class-ID: 0300
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Mobile] vendor: Dell
    driver: N/A pcie: speed: 8 GT/s lanes: 16 bus-ID: 01:00.0
    chip-ID: 10de:1c8d class-ID: 0300
  Device-3: Realtek Integrated Webcam type: USB driver: uvcvideo
    bus-ID: 1-12:4 chip-ID: 0bda:568a class-ID: 0e02 serial: <filter>
  Display: x11 server: X.Org v: 1.21.1.4 compositor: xfwm v: 4.16.1 driver:
    X: loaded: modesetting unloaded: fbdev,vesa gpu: i915 display-ID: :0.0
    screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96 s-size: 508x285mm (20.0x11.2")
    s-diag: 582mm (22.9")
  Monitor-1: eDP-1 model: Chi Mei Innolux res: 1920x1080 hz: 60 dpi: 142
    size: 344x193mm (13.5x7.6") diag: 394mm (15.5") modes: 1920x1080
  OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2)
    v: 4.6 Mesa 22.2.5-0ubuntu0.1~22.04.3 direct render: Yes
Audio:
  Device-1: Intel CM238 HD Audio vendor: Dell driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:a171 class-ID: 0403
  Device-2: NVIDIA GP107GL High Definition Audio vendor: Dell
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 16
    bus-ID: 01:00.1 chip-ID: 10de:0fb9 class-ID: 0403
  Sound Server-1: ALSA v: k5.19.0-46-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Dell driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1
    port: d000 bus-ID: 02:00.0 chip-ID: 10ec:8168 class-ID: 0200
  IF: enp2s0 state: down mac: <filter>
  Device-2: Intel Wireless 3165 driver: iwlwifi v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 bus-ID: 03:00.0 chip-ID: 8086:3165 class-ID: 0280
  IF: wlp3s0 state: up mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 1-4:3 chip-ID: 8087:0a2a class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.2 sub-v: 1000 hci-v: 4.2 rev: 1000
Drives:
  Local Storage: total: 1.03 TiB used: 62.2 GiB (5.9%)
  ID-1: /dev/nvme0n1 vendor: KingSpec model: NE-128 size: 119.24 GiB
    speed: 31.6 Gb/s lanes: 4 type: SSD serial: <filter> rev: SN07202
    temp: 39.9 C scheme: GPT
  ID-2: /dev/sda vendor: Toshiba model: MQ02ABD100H size: 931.51 GiB
    speed: 6.0 Gb/s type: HDD rpm: 5400 serial: <filter> rev: 1D scheme: GPT
Partition:
  ID-1: / size: 116.32 GiB used: 62.2 GiB (53.5%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 66.0 C pch: 49.0 C mobo: 40.0 C sodimm: SODIMM C
  Fan Speeds (RPM): cpu: 3237
Repos:
  Packages: 2322 apt: 2295 flatpak: 14 snap: 13
  Active apt repos in: /etc/apt/sources.list
    1: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy main restricted
    2: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy-updates main restricted
    3: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy universe
    4: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy-updates universe
    5: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy multiverse
    6: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
    7: deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) jammy-backports main restricted universe multiverse
    8: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security main restricted
    9: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
    10: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/atareao-ubuntu-atareao-jammy.list
    1: deb [https://ppa.launchpadcontent.net/atareao/atareao/ubuntu/](https://ppa.launchpadcontent.net/atareao/atareao/ubuntu/) jammy main
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list
    1: deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-jammy.list
    1: deb [https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/) jammy main
  Active apt repos in: /etc/apt/sources.list.d/gregory-hainaut-ubuntu-pcsx2_official_ppa-jammy.list
    1: deb [https://ppa.launchpadcontent.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/](https://ppa.launchpadcontent.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/) jammy main
  Active apt repos in: /etc/apt/sources.list.d/libretro-ubuntu-stable-jammy.list
    1: deb [https://ppa.launchpadcontent.net/libretro/stable/ubuntu/](https://ppa.launchpadcontent.net/libretro/stable/ubuntu/) jammy main
  Active apt repos in: /etc/apt/sources.list.d/makedeb.list
    1: deb [signed-by=/usr/share/keyrings/makedeb-archive-keyring.gpg arch=all] [https://proget.makedeb.org](https://proget.makedeb.org) makedeb main
  Active apt repos in: /etc/apt/sources.list.d/winehq-jammy.sources
    1: deb [arch=amd64 i386] [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) jammy main
Info:
  Processes: 209 Uptime: 7m wakeups: 1 Memory: 7.62 GiB
  used: 2.25 GiB (29.5%) Init: systemd v: 249 runlevel: 5 Compilers:
  gcc: 11.3.0 alt: 11/12 Shell: Bash v: 5.1.16 running-in: xfce4-terminal
  inxi: 3.3.13
```

---

