---
title: "Dual monitors: Primary Display (1) defaults to Secondary monitor (2)"
date: 2022-11-08
forum: Desktop Environments
---

### Post by makem2 on 2022-11-08
My setup:

```

makem@makem2204:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.1 LTS"
makem@makem2204:~$ echo $XDG_CURRENT_DESKTOP
XFCE
makem@makem2204:~$ sudo lshw -C display
[sudo] password for makem: 
  *-display                 
       description: VGA compatible controller
       product: GA106 [GeForce RTX 3060 Lite Hash Rate]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:400-3ff iomemory:400-3ff irq:195 memory:a0000000-a0ffffff memory:4000000000-400fffffff memory:4010000000-4011ffffff ioport:3000(size=128) memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 2
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080
makem@makem2204:~$ nvidia-settings


(nvidia-settings:4582): GLib-GObject-CRITICAL **: 15:42:37.981: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 15:42:38.099: PRIME: No offloading required. Abort
** Message: 15:42:38.099: PRIME: is it supported? no




```

I am using NVIDIA  driver metapackage from nvidia-driver -510 (proprietary)

Settings as shown in 'Display':

Primary Display (1):
DP-0
Microstep 24"
Refresh Rate 143.9 Hz

Secondary Display (2):
HDMI-0
ASUS 24"
Refresh Rate 60.0 Hz

I don't know how to output NVIDIA settings but in Xvideo settings 'Sync to this display device' is set to 'Auto'  with an option to choose (1) or (2) when Xvideo Sync To Vblank is enabled.

Dual booting xubuntu and windows 10:

On boot, grub displays on (1). Choosing xubuntu desktop from the menu gives the desktop on (2) with (1) blank.

Choosing a web page or LibreOffice via a panel icon on (2) gives them both on (1)

Choosing  'Display' or Terminal on (2) shows them both on (2)

Windows gets the displays correct.

Can anyone point me to resolve my xubuntu desktop to the primary display (1) on boot?

Edit: I just realised that when I moved house I put the Secondary screen on the left, whereas before the move it was on the right and everything worked fine. Not sure if that helps.

---

### Post by makem2 on 2022-11-14
[COLOR=#333333][FONT=&quot]Seems to be a bug in gnome, should be reported to ubuntu bugzilla. So sayeth:

[https://forums.developer.nvidia.com/t/unable-to-make-the-right-hand-monitor-primary-in-dual-monitor-setup/233660](https://forums.developer.nvidia.com/t/unable-to-make-the-right-hand-monitor-primary-in-dual-monitor-setup/233660)
[/FONT][/COLOR]

---

### Post by makem2 on 2022-11-15
[COLOR=#000000][FONT=Verdana]See thread:[/FONT][/COLOR]

[https://forum.xfce.org/viewtopic.php?pid=69719#p69719](https://forum.xfce.org/viewtopic.php?pid=69719#p69719)

[COLOR=#000000][FONT=Verdana]Which in 3 operations withstands a reboot.[/FONT][/COLOR]

---

