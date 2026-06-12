---
title: "Counter Strike Source frame skip problem"
date: 2019-05-14
forum: Gaming &amp; Leisure
---

### Post by sinisab89 on 2019-05-14
Hi!
Does anyone in here still plays CSS? :D I got a weird issue. My game skips a frame with every loud gun shot even though FPS doesnt drop. It feels like stuttering whenever I, or anybody who is close to me, shoots a gun. It doesnt matter if I have 300fps or 100fps it's always happening the same way. It gets really bad when people are spraying around, especially with P90. Only way to stop this behaviour is to turn on VSync but then I have really bad mouse input lag. Other games work just fine...

My system is Linux Mint 19.1, default kernel 4.15.0-48-generic. 

inxi-Fxz
```
System:
  Host: sinisab89-MS-7786 Kernel: 4.15.0-48-generic x86_64 bits: 64 
  compiler: gcc v: 7.3.0 Desktop: Cinnamon 4.0.10 
  Distro: Linux Mint 19.1 Tessa base: Ubuntu 18.04 bionic 
Machine:
  Type: Desktop Mobo: MSI model: A55M-P33 (MS-7786) v: 1.0 serial: <filter> 
  UEFI: American Megatrends v: 2.0 date: 02/04/2013 
CPU:
  Topology: Quad Core model: AMD Athlon II X4 631 bits: 64 type: MCP 
  arch: Fusion L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 sse4a svm bogomips: 20762 
  Speed: 1440 MHz min/max: 800/2600 MHz Core speeds (MHz): 1: 1440 2: 1780 
  3: 1928 4: 1924 
Graphics:
  Device-1: AMD Curacao PRO [Radeon R7 370 / R9 270/370 OEM] 
  vendor: PC Partner Limited driver: radeon v: kernel bus ID: 01:00.0 
  Display: x11 server: X.Org 1.19.6 driver: ati,radeon 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD PITCAIRN (DRM 2.50.0 4.15.0-48-generic LLVM 8.0.0) 
  v: 4.5 Mesa 19.0.1 - padoka PPA direct render: Yes 
Audio:
  Device-1: AMD FCH Azalia vendor: Micro-Star MSI driver: snd_hda_intel 
  v: kernel bus ID: 00:14.2 
  Device-2: AMD Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] 
  vendor: PC Partner Limited driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k4.15.0-48-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Micro-Star MSI driver: r8169 v: 2.3LK-NAPI port: d000 
  bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.38 TiB used: 594.44 GiB (42.1%) 
  ID-1: /dev/sda vendor: Western Digital model: WD15EARS-00MVWB0 
  size: 1.36 TiB 
  ID-2: /dev/sdb type: USB model: USB 2.0 USB Flash Drive size: 14.47 GiB 
Partition:
  ID-1: / size: 302.84 GiB used: 48.37 GiB (16.0%) fs: ext4 dev: /dev/sda3 
  ID-2: swap-1 size: 3.72 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 20.1 C mobo: N/A gpu: radeon temp: 39 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 209 Uptime: 1h 25m Memory: 7.77 GiB used: 1.73 GiB (22.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.19 
  inxi: 3.0.27 

```

---

### Post by sinisab89 on 2019-07-10
Few days ago I switched to Ubuntu 18.04 and on the way figured out that AMD's TearFree option is causing the game stuttering. Unfortunately I need TearFree On for my browser to play videos properly, without tearing. I have made two bash scripts that switch TearFree on and off on the fly.

tearfreeoff.sh
```
#!/bin/sh
#Turning off TearFree
xrandr --output DVI-D-1  --set TearFree off
```
tearfreeon
```
#!/bin/sh
#Turning on TearFree
xrandr --output DVI-D-1  --set TearFree on
```

Scripts work as intended. Now, I don't know how could I autorun them on game launch and on game exit so that tearfree switches off when I play the game and turns back on when i dont. Can someone help me?

---

### Post by g7x on 2020-02-15
I have before win7, after change in linux get worse results in games. then i use windows7 in steam counter strike source was get 50fps, after change in lubuntu now have just 20fps. dont use vine, or other emulators. I was tried other distributions like Linux mint, Ubuntu, manjaro, debian..... and get same bad results.
laptop samsung q330 
intel i3 370m 2.4ghz
graphic intel integrated in processor

Somebody can help me?!

---

### Post by wildmanne39 on 2020-02-16
Old thread back to sleep.

---

