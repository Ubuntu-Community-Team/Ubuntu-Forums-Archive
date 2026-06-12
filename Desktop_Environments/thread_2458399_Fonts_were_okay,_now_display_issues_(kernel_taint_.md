---
title: "Fonts were okay, now display issues (kernel taint ?)"
date: 2021-02-23
forum: Desktop Environments
---

### Post by oygle on 2021-02-23
Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-65-generic
OS Type: 64-bit
Processors: 4 × Intel® Core&#8482; i7-4510U CPU @ 2.00GHz
Memory: 7.7 GiB of RAM

Graphics Processor:  GeForce 840M
NVIDIA Driver Version: 460.32.03
Laptop screen:  1280 x 720

Global theme: Kubuntu
Plasma style:  Kubuntu
Fonts : Noto Sans 12 pt
GNOME/GTK app style:  Adwaita
-------------------------------------------------------

Firstly, I must say that for every prior version of Kubuntu, I have NEVER had to change fonts, themes, display properties. It always worked just fine out of the box. But with 20.04, the problems appeared.

I had to do a lot of research, changing themes, fonts, etc, new themes, addressing problems with GTK based apps, installing Nvidia drivers (which I have never had to do), and it was basically okay up until a few days ago.  Then just booted and it was all a mess again, what caused that I have no idea. The fonts are much larger and not much fits into the display now.

There was a hardware device application update, not sure if that had any bearing ? Why I mention that is because I did have Nvidia 455 driver installed, yet when I did a 

```
ubuntu-drivers devices
```

it recommended 460. So that got installed, no difference though. I even installed "gnome-tweaks" in desparation ..lol

There is only one GTK applications I run, Claws-Mail. That has its own theme, fonts setting, yet even that got totally messed up, huge fonts, a real mess.

Now, to some questions:

1. Do I really need to Nvidia driver ? I ask that because I have not had to install it in prior releases.

2. Is there a method I can use to, the KIS principle would be nice. For instance, why can't I just have a system wide theme, font, colour,etc setting and ALL applications use that ?  I say that because I have had to modify Terminal, OpenOffice, Kate, Dolphin,etc,etc, in regards to fonts. That was all basically okay, but now a mess again.

From ```
journalctl -b
``` a list at [https://pastebin.ubuntu.com/p/KQJDfxKjc7/](https://pastebin.ubuntu.com/p/KQJDfxKjc7/)

From ```
inxi -Fzx
``` ..

> 
System:    Kernel: 5.4.0-65-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: KDE Plasma 5.18.5 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Portable System: Dell product: Inspiron 3542 v: N/A serial: <filter> 
           Mobo: Dell model: 0WW73H v: A16 serial: <filter> BIOS: Dell v: A16 date: 09/02/2020 
Battery:   ID-1: BAT0 charge: 41.0 Wh condition: 41.0/41.4 Wh (99%) model: SMP-SDI2.8 DELL FW1MN31 
           status: Full 
CPU:       Topology: Dual Core model: Intel Core i7-4510U bits: 64 type: MT MCP arch: Haswell rev: 1 
           L2 cache: 4096 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 15962 
           Speed: 863 MHz min/max: 800/3100 MHz Core speeds (MHz): 1: 798 2: 798 3: 798 4: 799 
Graphics:  Device-1: Intel Haswell-ULT Integrated Graphics vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GM108M [GeForce 840M] vendor: Dell driver: nvidia v: 460.32.03 bus ID: 08:00.0 
           Display: x11 server: X.Org 1.20.9 driver: modesetting,nvidia unloaded: fbdev,nouveau,vesa 
           resolution: 1280x720~60Hz 
           OpenGL: renderer: GeForce 840M/PCIe/SSE2 v: 4.6.0 NVIDIA 460.32.03 direct render: Yes 
Audio:     Device-1: Intel Haswell-ULT HD Audio vendor: Dell driver: snd_hda_intel v: kernel bus ID: 00:03.0 
           Device-2: Intel 8 Series HD Audio vendor: Dell driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.4.0-65-generic 
Network:   Device-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter vendor: Dell driver: ath9k 
           v: kernel port: f040 bus ID: 06:00.0 
           IF: wlp6s0 state: down mac: <filter> 
           Device-2: Realtek RTL810xE PCI Express Fast Ethernet vendor: Dell driver: r8169 v: kernel 
           port: e000 bus ID: 07:00.0 
           IF: enp7s0 state: down mac: <filter> 
           Device-3: Qualcomm Atheros type: USB driver: btusb bus ID: 1-1.6:11 
           IF-ID-1: usb0 state: unknown speed: N/A duplex: N/A mac: <filter> 
Drives:    Local Storage: total: 931.51 GiB used: 247.53 GiB (26.6%) 
           ID-1: /dev/sda vendor: Seagate model: ST1000LM024 HN-M101MBB size: 931.51 GiB temp: 31 C 
Partition: ID-1: / size: 16.19 GiB used: 8.58 GiB (53.0%) fs: ext4 dev: /dev/sda1 
           ID-2: /home size: 894.99 GiB used: 238.95 GiB (26.7%) fs: ext4 dev: /dev/sda6 
           ID-3: swap-1 size: 4.66 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 50.0 C mobo: 51.0 C gpu: nvidia temp: 46 C 
           Fan Speeds (RPM): cpu: 0 
Info:      Processes: 212 Uptime: 4h 35m Memory: 7.68 GiB used: 2.07 GiB (26.9%) Init: systemd runlevel: 5 
           Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 




Is the "kernel taint" serious ?

---

