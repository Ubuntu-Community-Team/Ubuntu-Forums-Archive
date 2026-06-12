---
title: "Tearfree option crashes Xorg"
date: 2019-05-10
forum: Desktop Environments
---

### Post by ytterbious on 2019-05-10
Whenever I turn on the option Tearfree in Xorg (through xorg.conf, or 10- or 20-radeon.conf), Xorg crashes on reboot. The code is:
```
[B]Section "Device"
    Identifier "Radeon"
    Driver "radeon"
    Option "TearFree" "on"
EndSection[/B]
```

I'm getting awful screen tearing in Cemu through Playonlinux and adding the window in CompizConfig General > Composite > Unredirect match does nothing.

---

### Post by him610 on 2019-05-11
Please show results, within code tags, of *inxi -Fxz*

---

### Post by ytterbious on 2019-05-11
```
System:    Host: Sys-1 Kernel: 4.18.0-18-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu3)
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: B150M-A D3 v: Rev X.0x serial: N/A
           UEFI: American Megatrends v: 2604 date: 02/21/2018
CPU:       Quad core Intel Core i7-7700K (-MT-MCP-) 
           arch: Skylake rev.9 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 33600
           clock speeds: max: 4500 MHz 1: 4399 MHz 2: 4399 MHz 3: 4399 MHz
           4: 4399 MHz 5: 4399 MHz 6: 4399 MHz 7: 4399 MHz 8: 4399 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Hawaii PRO [Radeon R9 290/390]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.1 ) driver: amdgpu
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: AMD Radeon R9 200 Series (HAWAII, DRM 3.26.0, 4.18.0-18-generic, LLVM 9.0.0)
           version: 4.5 Mesa 19.1.0-devel - padoka PPA Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Hawaii HDMI Audio [Radeon R9 290/290X / 390/390X]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 100 Series/C230 Series Family HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.18.0-18-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 04:00.0
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 7033.1GB (13.6% used)
           ID-1: /dev/sdb model: WDC_WD10EURX size: 1000.2GB temp: 40C
           ID-2: /dev/sda model: TOSHIBA_HDWE160 size: 6001.2GB temp: 45C
           ID-3: USB /dev/sdc model: USB_Flash_Drive size: 16.0GB temp: 0C
           ID-4: USB /dev/sdd model: Cruzer_Fit size: 15.7GB temp: 0C
Partition: ID-1: / size: 19G used: 9.5G (55%) fs: ext4 dev: /dev/sda3
           ID-2: /home size: 4.7T used: 801G (18%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 80.23GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 77.0C mobo: 27.8C gpu: 63.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 404 Uptime: 11:05 Memory: 13039.9/32093.2MB
           Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```

---

### Post by mc4man on 2019-05-11
Don't know anything about amd gpu's but noticed you're setting driver "radeon" but actually using the opensource one, amdgpu

---

### Post by him610 on 2019-05-11
I am not familiar with Cemu, Playonlinux, or CompizConfig. Sometimes to solve a problem, it is best to get back to the basic system.

You are using the amdgpu driver. There is also a amdgpu-pro driver that can be downloaded from AMD. You can read about it here, [https://www.amd.com/en/support/kb/release-notes/rn-radpro-lin-16-40]("https://www.amd.com/en/support/kb/release-notes/rn-radpro-lin-16-40")
I don't know if it will help resolve your issue, but it may be worth a try.

---

### Post by him610 on 2019-05-11
This is the reference page for the amdgpu driver.
[https://wiki.archlinux.org/index.php/AMDGPU#AMDGPU_PRO]("https://wiki.archlinux.org/index.php/AMDGPU#AMDGPU_PRO")

As you can see you should have amdgpu instead of radeon in the Device Section of /etc/X11/xorg.conf.d/10-screen.conf

---

