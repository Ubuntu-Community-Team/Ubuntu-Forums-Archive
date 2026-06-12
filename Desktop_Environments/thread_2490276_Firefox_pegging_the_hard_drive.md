---
title: "Firefox pegging the hard drive"
date: 2023-08-28
forum: Desktop Environments
---

### Post by peyre on 2023-08-28
I'm running the LTS of Xubuntu on an older machine (~2009), and it works great most of the time.  However, once in a while, something (pretty sure it's Firefox) starts churning the SSD and slows the computer to such a crawl that the cursor barely responds to the mouse.  I haven't been able to close any applications once it does this; my only option is to hit the Reset button or do a hard shutdown.  I have maybe 10-20 tabs open in Firefox, not dozens.  Anyone have any ideas for fixing this, or mitigating it somewhat?

---

### Post by ajgreeny on 2023-08-28
Hardware details will probably help.
20 tabs in Firefox will eat a lot of RAM so show the output of command ***inxi -Fzx*** and we can move on from there.

---

### Post by peyre on 2023-08-29
Sounds good.  Here's what it returns:

> System:
  Kernel: 5.15.0-79-generic x86_64 bits: 64 compiler: gcc v: 11.3.0
    Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: Gigabyte product: G31M-ES2L v: N/A
    serial: <superuser required>
  Mobo: Gigabyte model: G31M-S2L v: x.x serial: <superuser required>
    BIOS: Award v: F10 date: 09/29/2009
CPU:
  Info: dual core model: Pentium E5200 bits: 64 type: MCP
    arch: Core Yorkfield rev: 6 cache: L1: 128 KiB L2: 2 MiB
  Speed (MHz): avg: 2105 high: 2452 min/max: 1200/2500 cores: 1: 1759
    2: 2452 bogomips: 10001
  Flags: ht lm nx pae sse sse2 sse3 ssse3
Graphics:
  Device-1: AMD Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
    driver: amdgpu v: kernel bus-ID: 01:00.0
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,vesa gpu: amdgpu resolution: 1: 1280x1024~60Hz
    2: 1280x1024~60Hz
  OpenGL: renderer: AMD Radeon RX 550 / 550 Series (polaris12 LLVM 15.0.7
    DRM 3.42 5.15.0-79-generic)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel NM10/ICH7 Family High Definition Audio
    vendor: Gigabyte GA-D525TUD driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Device-2: AMD Baffin HDMI/DP Audio [Radeon RX 550 640SP / 560/560X]
    driver: snd_hda_intel v: kernel bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.15.0-79-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Gigabyte driver: r8169 v: kernel port: be00 bus-ID: 03:00.0
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Bluetooth:
  Device-1: ASUSTek Broadcom BCM20702A0 Bluetooth type: USB driver: btusb
    v: 0.8 bus-ID: 3-2:2
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.0
Drives:
  Local Storage: total: 1.83 TiB used: 960.2 GiB (51.2%)
  ID-1: /dev/sdb vendor: SanDisk model: SDSSDH3 512G size: 476.94 GiB
  ID-2: /dev/sdc vendor: Samsung model: HD154UI size: 1.36 TiB
Partition:
  ID-1: / size: 467.89 GiB used: 139.45 GiB (29.8%) fs: ext4 dev: /dev/sdb3
  ID-2: /boot/efi size: 512 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sdb2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 60.5 MiB (3.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 66.0 C mobo: N/A gpu: amdgpu temp: 47.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 261 Uptime: 2h 13m Memory: 3.82 GiB used: 2.4 GiB (62.8%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2979 Shell: Bash
  v: 5.1.16 inxi: 3.3.13


---

### Post by TenPlus1 on 2023-08-29
A friend recommended this which helped a lot with system stuttering and Firefox memory use:

First edit your /etc/sysctl.conf file and add this line to the end, save and reboot:

vm.swappiness=15

Then in Firefox type about:config in the address bar to enter settings mode and change the following:

browser.cache.memory.enable (false)

browser.cache.disk.enable (false)

network.prefetch-next (false)

browser.sessionhistory.max_total_viewers (0)

browser.sessionstore.interval (600000)

This lowers memory use for Firefox, sorts out virtual memory allocation and helps the system run a little smoother.

---

### Post by peyre on 2023-08-29
Thanks!  I'll try that tonight.  I probably won't know for some time whether this fixes it, since it's intermittent and usually strikes on weekends, when I use the computer the most.  So I think I'll mark it solved, at least for now; I'll *unsolve* it if it keeps happening.  I appreciate your assistance with this!

Edit: Yesterday (9/3) I managed to close Firefox before it really tied up the SDD.  Maybe maybe the changes made the difference here! (Or maybe I just happened to catch it in time.)

---

