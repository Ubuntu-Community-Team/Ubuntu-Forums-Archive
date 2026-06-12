---
title: "Steam won't start"
date: 2016-04-22
forum: Gaming &amp; Leisure
---

### Post by Blix775 on 2016-04-22
Hi! I just downloaded Ubuntu 16.04 and installed the AMD proprietary drivers and installed steam. Steam will never show on the screen but when I check the running programs with ps aux it shows steam running. I tried starting it from the cli and this is the error message it shows:
> Running Steam on ubuntu 16.04 64-bitSTEAM_RUNTIME is enabled automatically
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2016-04-22 03:19:20] Startup - updater built Mar 29 2016 17:40:06
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

Here is the system info:
> System:    Host: snes Kernel: 4.4.0-21-generic x86_64 (64 bit gcc: 5.3.1)           Desktop: Cinnamon 2.8.6 (Gtk 3.18.9-1ubuntu3)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: AM1M-S2H v: x.x
           Bios: American Megatrends v: F1 date: 01/27/2014
CPU:       Quad core AMD Athlon 5350 APU with Radeon R3 (-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 16369
           clock speeds: max: 2050 MHz 1: 1400 MHz 2: 1650 MHz 3: 800 MHz
           4: 1000 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series]
           bus-ID: 00:01.0
           Display Server: X.Org 1.18.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD KABINI (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-21-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 01:00.0
           IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (22.1% used)
           ID-1: /dev/sda model: TOSHIBA_MK1655GS size: 120.0GB temp: 33C
Partition: ID-1: / size: 30G used: 5.7G (20%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 76G used: 16G (22%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 4.10GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 21.4C mobo: N/A gpu: 20.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 230 Uptime: 29 min Memory: 1721.0/3390.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.35 




I found this post on steamcommunity which claims the same thing happens in arch linux. 
[https://steamcommunity.com/app/221410/discussions/0/617336568068489642/](https://steamcommunity.com/app/221410/discussions/0/617336568068489642/)

If anyone knows how to solve this, please let me know. 

PD: I uninstalled steam and reinstalled it and the old icon on the desktop is now broken (showing a blank page instead of the icon) but it won't go away.

---

### Post by MikeCyber on 2016-04-22
Maybe this?
[URL="https://bbs.archlinux.org/viewtopic.php?id=193802"]https://bbs.archlinux.org/viewtopic.php?id=193802

[/URL]I have Nvidia... I also would try a different steam probably download from steam site. Remove first in your home the hidden steam folder: ~./steam
Also never use sudo unless you have to.

---

### Post by Sableyes on 2016-04-22
Hullo. I also have an AMD Kabini (8120 I think).

I have had issues starting steam on every Ubuntu release since 14.04 after install, even when upgrading between distros, and the below has always fixed it.

cd $HOME/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak
cd $HOME/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak

Linky : [http://sableyes.co.uk/?p=2479](http://sableyes.co.uk/?p=2479)

---

### Post by Blix775 on 2016-04-24
Thanks a lot. My computer with an nvidia gpu has not had any problems.
When I try that first command it says
"No such file or directory"
I suppose I am missing some libraries then?

---

### Post by Mr.Dunham on 2016-04-24
> **Blix775 said:**
> Thanks a lot. My computer with an nvidia gpu has not had any problems.
When I try that first command it says
"No such file or directory"
I suppose I am missing some libraries then?

Go into your home directory, enable the "Show hidden files" option and look for your .steam directory, to see if you find your own path to ".steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu" as your path might be different.

---

### Post by Blix775 on 2016-04-24
This is the path I found. 
"/home/blix/.steam/steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu"
Can I just copy them from the gui?

Edit: These are the items in that folder. 

"libfreetype.so.6      libX11.so.6.3.0  libXdmcp.so.6      libXinerama.so.1.0.0libfreetype.so.6.8.0  libXau.so.6      libXdmcp.so.6.0.0  libXrandr.so.2
libstdc++.so.6        libXau.so.6.0.0  libXext.so.6       libXrandr.so.2.2.0
libstdc++.so.6.0.18   libxcb.so.1      libXext.so.6.4.0   libXrender.so.1
libX11.so.6           libxcb.so.1.1.0  libXinerama.so.1   libXrender.so.1.3.0
"
I just realized that the amd64 folder is missing. Do I have to create it?

---

### Post by MikeCyber on 2016-04-24
You can copy etc. in a terminal but I would first move the whole .steam to f.ex. .steamOld and try again with another steam probably download from steam.

---

