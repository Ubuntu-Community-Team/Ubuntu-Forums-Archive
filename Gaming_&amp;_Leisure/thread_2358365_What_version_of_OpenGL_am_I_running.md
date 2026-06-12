---
title: "What version of OpenGL am I running"
date: 2017-04-12
forum: Gaming &amp; Leisure
---

### Post by Richard_Romick on 2017-04-12
I have installed the oibaf PPA for MESA, but I am a little confused about which version of OpenGL I am currently running.  I have Googled the issue, but I can't seem to get a straight answer.  My glxinfo and system information is down below.  Should I base my current OpenGL version off the core profile version string (which would be 4.5) or the version string (3.0).

Additionally, if I have installed oibaf correctly, I wonder if I can get more performance if I switch to padoka.  I know it is unstable, but I am trying to run Pillars of Eternity and getting poor performance (should run a lot better considering it is just animations on pre-rendered backgrounds).  I realize that Unity, which PoE is built on, has poor performance on low end systems like this.

I appreciate any help you can give me.  Thanks in advance for your time.

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 620 (Kaby Lake GT2) 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.1.0-devel
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.1.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 17.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

System:    Host: richard-Lemur Kernel: 4.8.0-46-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3.2) Distro: Ubuntu 16.04 xenial
Machine:   System: System76 (portable) product: Lemur v: lemu7
           Mobo: System76 model: Lemur v: lemu7 Bios: American Megatrends v: 5.12 date: 02/17/2017
CPU:       Dual core Intel Core i7-7500U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11600
           clock speeds: max: 3500 MHz 1: 527 MHz 2: 574 MHz 3: 581 MHz 4: 574 MHz
Graphics:  Card: Intel Device 5916 bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 driver: intel Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           GLX Version: 3.0 Mesa 17.1.0-devel Direct Rendering: Yes
Audio:     Card Intel Device 9d71 driver: snd_hda_intel bus-ID: 00:1f.3 Sound: ALSA v: k4.8.0-46-generic
Network:   Card-1: Intel Device 24fd driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: up speed: N/A duplex: N/A mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 03:00.1
           IF: enp3s0f1 state: down mac: <filter>
Drives:    HDD Total Size: 628.1GB (14.8% used) ID-1: /dev/sda model: Samsung_SSD_840 size: 500.1GB
           ID-2: /dev/sdb model: TOSHIBA_THNSNJ12 size: 128.0GB
Partition: ID-1: / size: 109G used: 13G (12%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 124M (28%) fs: ext2 dev: /dev/sdb2
           ID-3: /home size: 459G used: 67G (16%) fs: ext4 dev: /dev/sda1
           ID-4: swap-1 size: 8.51GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 231 Uptime: 9:42 Memory: 1225.7/7906.3MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (fish) inxi: 2.2.35

---

