---
title: "Screen Flicker problem with RX 560 GPU in ubuntu 18.04"
date: 2018-09-20
forum: Desktop Environments
---

### Post by toaki on 2018-09-20
I am using amd ryzen R7 1700 cpu and RX 560 GPU...  After Installing Ubuntu 18.04 my monitor screen is always flickering. I have a HDMI connection with my gpu  any solution for my problem?
> 
System:    Host: astrex Kernel: 4.15.0-34-generic x86_64 bits: 64
           Console: tty 0 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Gigabyte product: AB350-Gaming 3 serial: N/A
           Mobo: Gigabyte model: AB350-Gaming 3-CF v: x.x serial: N/A
           UEFI [Legacy]: American Megatrends v: F23 date: 08/08/2018
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-)
           speed/max: 1369/3400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Baffin [Polaris11]
           Display Server: X.Org 1.19.6
           drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
           Resolution: 1920x1080@74.97hz
           OpenGL: renderer: Radeon RX 560 Series
           version: 4.6.13536 18.30.2.15
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 3250.7GB (38.3% used)
Info:      Processes: 373 Uptime: 42 min Memory: 2721.6/16053.7MB
           Client: Shell (sudo) inxi: 2.3.56 



---

### Post by dbergst on 2018-09-20
I believe the correct driver for amd baffin polaris 11 is amdgpu.  The ati driver is for older hardware.

---

### Post by toaki on 2018-09-20
The flickering is stop for now...
 I don't know how but my best guessing is that I turned of the VSYNC in my monitor and reduced its refresh rate 75Hz to 60 Hz this do the trick.

---

### Post by wildmanne39 on 2018-09-23
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

