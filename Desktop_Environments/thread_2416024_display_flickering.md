---
title: "display flickering"
date: 2019-04-04
forum: Desktop Environments
---

### Post by m.eraj1995 on 2019-04-04
Dear Sir,

on my system display is flickering ,

Thanks,

---

### Post by kc1di on 2019-04-04
We need more info on your machine and video card. in a terminal do this ```
sudo apt install inxi
``` when that is finished issue this command in terminal and post output here. ```
inxi -Fxz
``` Please post using code tags.

---

### Post by m.eraj1995 on 2019-04-04
root@administrator:~# inxi -Fxz
System:
  Host: administrator Kernel: 4.18.0-16-generic x86_64 bits: 64 
  compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.2 
  Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: Intel model: DH61WW v: AAG23116-203 
  serial: <filter> BIOS: Intel v: BEH6110H.86A.0016.2011.0118.1128 
  date: 01/18/2011 
CPU:
  Topology: Dual Core model: Intel Core i3-2100 bits: 64 type: MT MCP 
  arch: Sandy Bridge rev: 7 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 24743 
  Speed: 1599 MHz min/max: 1600/3100 MHz Core speeds (MHz): 1: 1598 
  2: 1632 3: 1596 4: 1596 
Graphics:
  Device-1: Intel 2nd Generation Core Processor Family Integrated 
  Graphics 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: server: X.Org 1.20.1 driver: i915 resolution: 1360x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel Sandybridge Desktop 
  v: 3.3 Mesa 18.2.8 direct render: Yes 
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k4.18.0-16-generic 
Network:
  Device-1: Intel 82579V Gigabit Network driver: e1000e v: 3.2.6-k 
  port: f060 bus ID: 00:19.0 
  IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  IF-ID-1: enp0s29u1u6c4i2 state: up speed: N/A duplex: N/A 
  mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 8.60 GiB (0.9%) 
  ID-1: /dev/sda vendor: Seagate model: ST1000DM003-1ER162 
  size: 931.51 GiB temp: 37 C 
Partition:
  ID-1: / size: 915.89 GiB used: 8.60 GiB (0.9%) fs: ext4 
  dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 36.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 249 Uptime: 4h 55m Memory: 1.79 GiB 
  used: 1.15 GiB (64.2%) Init: systemd runlevel: 5 Compilers: gcc: N/A 
  Shell: bash v: 4.4.19 inxi: 3.0.24

---

### Post by m.eraj1995 on 2019-04-06
Dear sir help me on this .

---

### Post by peter-a on 2019-04-08
My screen flickers too since 18.10 I think. Every so often, like a line of radio interference across the screen. I have 2 screens, it happens on both. I fitted ferrite cores to all the cables, no difference.

---

### Post by m.eraj1995 on 2019-04-11
No reply ???

---

### Post by m.eraj1995 on 2019-04-23
why there is no reply for this issue still i am facing display flickering issue when i scroll in browser .

---

