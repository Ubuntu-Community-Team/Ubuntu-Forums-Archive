---
title: "No video, sound or bluetooth on 22.04 bluetooth."
date: 2022-04-23
forum: Desktop Environments
---

### Post by mike010 on 2022-04-23
Hey,

I have a fresh install of Ubuntu 22.04 on install i said to install all the updates and the 3rd party drivers when i go to play a video it shut the player down or the just opens the player up with no video playing, 

On the Bluetooth where you go to turn the Bluetooth on the slider won't move and just doesn't connect. Booth of these are new problems cause i had 20.04 before and both worked great.

---

### Post by #&amp;thj^% on 2022-04-23
When you say Video, DVD? homemade, web content
open the player with the terminal EG:
"your-player-name"
add the video you say is blank

---

### Post by mike010 on 2022-04-23
There mp4 video's i ripped from some dvd's i got. I'm using totem video player.
Thank you.

---

### Post by jeremy31 on 2022-04-23
Any result in terminal for ```
dpkg -l | grep linux-modules-extra-($uname -r)
```

---

### Post by mike010 on 2022-04-23
No result using any of these commands

---

### Post by mike010 on 2022-04-23
I was just able to get a .avi file to play.

---

### Post by jeremy31 on 2022-04-23
Any results for ```
modinfo btusb; lsusb
```

---

### Post by mike010 on 2022-04-23
Nothing using those i ran up on a .avi file and that one played fine but when i went to just open totem it opened then just shut down.

---

### Post by jeremy31 on 2022-04-23
What result for ```
sudo apt install inxi && inxi -Fxxxz
```

---

### Post by mike010 on 2022-04-23
Sorry had to leave for a bit here's the output.

```
System:
  Kernel: 5.15.0-25-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.0 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3 42.0
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Desktop System: Dell product: Inspiron 3650 v: X00
    serial: <superuser required> Chassis: type: 3 serial: <superuser required>
  Mobo: Dell model: 0C2XKD v: A01 serial: <superuser required>
    UEFI-[Legacy]: Dell v: 3.2.3 date: 04/25/2016
Battery:
  Device-1: hidpp_battery_0
    model: Logitech Marathon Mouse/Performance Plus M705 serial: <filter>
    charge: 55% (should be ignored) rechargeable: yes status: Discharging
  Device-2: hidpp_battery_1 model: Logitech K350 serial: <filter>
    charge: 70% (should be ignored) rechargeable: yes status: Discharging
CPU:
  Info: dual core model: Intel Pentium G4400 bits: 64 type: MCP
    smt: <unsupported> arch: Skylake-S rev: 3 cache: L1: 128 KiB L2: 512 KiB
    L3: 3 MiB
  Speed (MHz): avg: 900 min/max: 800/3300 cores: 1: 900 2: 900
    bogomips: 13199
  Flags: ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel HD Graphics 510 vendor: Dell driver: i915 v: kernel ports:
    active: HDMI-A-1 empty: DP-1 bus-ID: 00:02.0 chip-ID: 8086:1902
    class-ID: 0300
  Device-2: Z-Star Micro Vimicro USB Camera (Altair) type: USB
    driver: uvcvideo bus-ID: 1-3:2 chip-ID: 0ac8:3450 class-ID: 0e02
  Display: wayland server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 display-ID: 0
  Monitor-1: HDMI-A-1 model: Sceptre E22 serial: <filter> res: 1920x1080
    dpi: 102 size: 521x293mm (20.5x11.5") diag: 546mm (21.5") modes:
    max: 1920x1080 min: 720x400
  OpenGL: renderer: Mesa Intel HD Graphics 510 (SKL GT1) v: 4.6 Mesa 22.0.1
    direct render: Yes
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio vendor: Dell
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a170
    class-ID: 0403
  Sound Server-1: ALSA v: k5.15.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Dell driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1
    port: e000 bus-ID: 02:00.0 chip-ID: 10ec:8168 class-ID: 0200
  IF: enp2s0 state: down mac: <filter>
  Device-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
    vendor: Dell Vostro 3470 driver: ath9k v: kernel pcie: speed: 2.5 GT/s
    lanes: 1 bus-ID: 03:00.0 chip-ID: 168c:0036 class-ID: 0280
  IF: wlp3s0 state: up mac: <filter>
Bluetooth:
  Device-1: Qualcomm Atheros type: USB driver: N/A bus-ID: 1-5:3
    chip-ID: 0cf3:e005 class-ID: e001
Drives:
  Local Storage: total: 1.36 TiB used: 25.1 GiB (1.8%)
  ID-1: /dev/sda vendor: Crucial model: CT500MX500SSD1 size: 465.76 GiB
    speed: 6.0 Gb/s type: SSD serial: <filter> rev: 033 scheme: MBR
  ID-2: /dev/sdb vendor: Toshiba model: DT01ACA100 size: 931.51 GiB
    speed: 6.0 Gb/s type: HDD rpm: 7200 serial: <filter> rev: A7S0 scheme: MBR
Partition:
  ID-1: / size: 455.9 GiB used: 25.1 GiB (5.5%) fs: ext4 dev: /dev/sda5
  ID-2: /boot/efi size: 512 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/sda3
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 29.8 C pch: 48.0 C mobo: 27.8 C
  Fan Speeds (RPM): cpu: 709 fan-1: 732
Info:
  Processes: 215 Uptime: 4m wakeups: 4 Memory: 15.54 GiB
  used: 2.14 GiB (13.8%) Init: systemd v: 249 runlevel: 5 Compilers: gcc: N/A
  Packages: 1725 apt: 1716 snap: 9 Shell: Bash v: 5.1.16
  running-in: gnome-terminal inxi: 3.3.13
mitch@mitch-Inspiron-3650:~$ inxi
CPU: dual core Intel Pentium G4400 (-MCP-) speed/min/max: 900/800/3300 MHz
Kernel: 5.15.0-25-generic x86_64 Up: 4m Mem: 2216.7/15911.8 MiB (13.9%)
Storage: 1.36 TiB (1.8% used) Procs: 214 Shell: Bash inxi: 3.3.13
```

---

### Post by him610 on 2022-04-23
FWIW: Bluetooth on 22.04 does work. I could detect no difference in its operation from LTS 20.04.+
```

$ Uld
Linux V3-572Ga 5.15.0-25-generic #25-Ubuntu SMP Wed Mar 30 15:54:22 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy
XFCE

```

---

