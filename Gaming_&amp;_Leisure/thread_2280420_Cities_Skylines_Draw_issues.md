---
title: "Cities: Skylines Draw issues"
date: 2015-05-30
forum: Gaming &amp; Leisure
---

### Post by Richard_Romick on 2015-05-30
I know that the Paradox forums are probably a better place to get advice on one of their games, but I haven't had much luck there getting Cities: Skylines to work, and was hoping the great people here would be more helpful.  Thanks for looking at my issue, here is what I posted there:

I am having an issue on Ubuntu where some menu items aren't being displayed (example: when selecting where to start your city, the selections don't highlight).  Also, some other objects aren't being displayed while playing (example: when building roads, the overlay that is supposed to apear showing you were the road is expected to be build doesn't show).  Lastly, objects like buildings and trees are only displayed at certain zoom levels, mainly when you are really close or really far away.

If anyone knows the answer to this problem, I would greatly appreciate it.

System:  Host: senlis-Galago-UltraPro Kernel: 3.13.0-52-generic x86_64 (64 bit, gcc: 4.8.2)
  Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:  System: System76 (portable) product: Galago UltraPro version: galu1
  Mobo: System76 model: Galago UltraPro version: galu1 Bios: American Megatrends version: 4.6.5 date: 07/09/2013
CPU:  Quad core Intel Core i7-4750HQ CPU (-HT-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15964.6
  Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz 3: 800.00 MHz 4: 800.00 MHz 5: 800.00 MHz 6: 1100.00 MHz 7: 1300.00 MHz 8: 1100.00 MHz
Graphics:  Card: Intel Crystal Well Integrated Graphics Controller bus-ID: 00:02.0
  X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz
  GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:  Card-1: Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
  Card-2: Intel Crystal Well HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
  Sound: Advanced Linux Sound Architecture ver: k3.13.0-52-generic
Network:  Card-1: Intel Wireless 7260 driver: iwlwifi ver: in-tree: bus-ID: 03:00.0
  IF: wlan0 state: up mac: <filter>
  Card-2: Intel Ethernet Connection I217-V driver: e1000e ver: 2.3.2-k port: f080 bus-ID: 00:19.0
  IF: eth0 state: down mac: <filter>
Drives:  HDD Total Size: 360.1GB (21.5% used) 1: id: /dev/sda model: Corsair_Force_GS size: 360.1GB temp: 34C
Partition: ID: / size: 322G used: 73G (24%) fs: ext4 ID: /boot size: 236M used: 124M (56%) fs: ext2
  ID: swap-1 size: 8.51GB used: 0.36GB (4%) fs: swap
RAID:  No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:  System Temperatures: cpu: 14.0C mobo: N/A
  Fan Speeds (in rpm): cpu: N/A
Info:  Processes: 381 Uptime: 17 days Memory: 2512.2/7908.4MB Runlevel: 2 Gcc sys: 4.8.2
  Client: Shell (bash 4.3.11) inxi: 1.9.17

---

### Post by Richard_Romick on 2015-06-01
Found the solution, which is to add this:

UNITY_DISABLE_GRAPHICS_DRIVER_WORKAROUNDS=yes %command%

to my launch options

---

### Post by oldrocker99 on 2015-06-02
It's a good idea (and forum etiquette) to add [SOLVED] to the header. Great that you found out how to solve it, and labelling the thread that way might help another user.

---

