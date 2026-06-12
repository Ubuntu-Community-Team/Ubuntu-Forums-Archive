---
title: "gnome-shell freezes"
date: 2019-03-31
forum: Desktop Environments
---

### Post by curts on 2019-03-31
I have been having problems with gnome-shell freezing in Ubuntu 18.04. When the display freezes, the mouse will still move normally, but mouse button clicks and keyboard entry don't appear to have any effect, because the windows are not updating. The freeze manifests itself in one of three forms:
[LIST]
[*]gnome-shell resets
[*]gnome-session high CPU usage
[*]Xorg high CPU usage
[/LIST]

**gnome-shell resets:** the display temporarily freezes for a number of seconds, then the mouse warps to the lower right quadrant of the screen and display updates resume. In the system log, one finds the NVIDIA driver has reset:
```
[ 1399.140318] NVRM: GPU at PCI:0000:01:00: GPU-34d7319c-5b19-1e75-186d-c187099e4fe5
[ 1399.140323] NVRM: Xid (PCI:0000:01:00): 32, Channel ID 00000009 intr 00800000
[ 1399.140655] NVRM: Xid (PCI:0000:01:00): 32, Channel ID 00000009 intr 00800000
```

**gnome-session high CPU usage:** recovery via <Alt>-<F2> is not possible, because the display is not updating. The OS is still operational and it is possible to login via ssh. Sometimes it is possible to recover using ```
killall -3 gnome-shell
```, but often times only once. If the killall fails, the user now likely has the third condition. If remote login is not available, the OS will respond to <Alt>-<Sys Rq>-REISUB.

**Xorg high CPU usage:** recovery via <Alt>-<F2> is not possible, because the display is not updating. The OS is still operational and it is possible to login via ssh. At this point I use 'kill -1' to gracefully shutdown applications before attempting to reboot. If the OS doesn't respond to 'sudo reboot' in a timely fashion or remote login is not available, the OS will respond to <Alt>-<Sys Rq>-REISUB.

In the past when I have had problems with 18.04, I would fall back to my 14.04 LTS install which is also configured with gnome-shell. Recently, it has started experiencing similar problems with slightly different symptoms. Instead of the display freezing for all but the mouse cursor, the entire display freezes, but will sporadically update little by little. With a lot of patience, a user can potentially close out a few key applications before rebooting. The OS will respond to <Alt>-<Sys Rq>-REISUB.

Since gnome-shell in 14.04 started experiencing problems, I next tried gnome fallback - Compiz and found it had the exact same problems. I tried both the NVIDIA 384.130 (latest) & 340.107 drivers in 14.04, but it didn't make any difference. In 18.04 I tried changing from the latest v390.116 driver to v340.107, only to end up with clobbered system that couldn't display gdm after the reboot. Fortunately, I always make an image backup of my system before attempting such changes, so I was able to quickly recover from the failed driver install. So, the NVIDIA driver install bug in the settings panel has returned to 18.04.

Next I tried gnome fallback - Metacity in 14.04 with the 384.130 driver, which is *completely stable* and is the desktop I am using now to compose this post.

Platform specs in 18.04 per inxi:
```
System:    Host: panther2 Kernel: 4.15.0-46-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-MA78GM-US2H serial: N/A
           BIOS: Award v: F9d date: 08/04/2010
CPU:       Triple core AMD Phenom 8650 (-MCP-) cache: 1536 KB
           clock speeds: max: 2300 MHz 1: 1150 MHz 2: 1150 MHz 3: 1150 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 550 Ti/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.116
Audio:     Card-1 NVIDIA GF116 High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 Creative Labs EMU10k2/CA0100/CA0102/CA10200 [Sound Blaster Audigy Series]
           driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.15.0-46-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full
           mac: 00:24:1d:26:fc:6d
Drives:    HDD Total Size: 2250.5GB (37.9% used)
           ID-1: /dev/sda model: SAMSUNG_HD502IJ size: 500.1GB
           ID-2: /dev/sdb model: ST1000DM003 size: 1000.2GB
           ID-3: /dev/sdc model: SAMSUNG_HD502IJ size: 500.1GB
           ID-4: /dev/sdd model: ST3250620A size: 250.1GB
Partition: ID-1: / size: 20G used: 13G (67%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 40G used: 31G (82%) fs: ext3 dev: /dev/sda5
           ID-3: swap-1 size: 4.29GB used: 0.00GB (0%)
           fs: swap dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 51.0C mobo: 41.0C gpu: 48C
           Fan Speeds (in rpm): cpu: 885 fan-1: 1700 fan-3: 0
Info:      Processes: 274 Uptime: 12 min Memory: 2183.5/16038.2MB
           Client: Shell (bash) inxi: 2.3.56 
```

Video h/w specs in 18.04:
```
  *-display
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:25 memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:dc000000-dfffffff ioport:ef00(size=128) memory:c0000-dffff
```

During my research I came across the information that the current gnome-shell has a known problem with "rapidly updating content". I was not displaying seconds in the panel clock, so that wasn't an issue. I changed the Conky update rate in my 18.04 desktop from 1s to 3s, but it didn't make a noticeable difference. My 14.04 desktop uses Screenlets to display system info.

The best way I have found to replicate the problem is to launch Firefox where it restores a sizable number of tabs from the previous session. If it doesn't cause the problem immediately, using the browser for a time generally does the trick eventually.

Best regards,

Curt

---

