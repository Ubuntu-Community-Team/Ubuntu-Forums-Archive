---
title: "Dual monitor setup dificulties"
date: 2021-10-29
forum: Desktop Environments
---

### Post by makem2 on 2021-10-29
I have two problems in using dual monitors:

1. If both monitors are connected on booting grub (one is Display Post and is primary and the other is HDMI), it hangs  and never gets to desktop.
If I try the same using Windows, it boots to the desktop but hangs and is never usable.

2. If I just connect the primary (Display Port) monitor, both grub and Windows boot normally. Even with the second monitor turned off grub still hangs. I must remove the cable.

If I plug in the HDMI cable AFTER booting grub, the second monitor takes over and the desktop completely moves to the second monitor. Setting the Primary monitor in Display settings makes no difference.

Searching around for a solution I found:

[https://www.instructables.com/How-to-set-up-multiple-monitors-in-linux/](https://www.instructables.com/How-to-set-up-multiple-monitors-in-linux/)

However, my xorg.conf file is at: /usr/share/doc/xserver-xorg-video-intel/ and it only contains:

```

Section "Device"
        Identifier "Intel"
        Driver "intel"
#       Option "AccelMethod" "uxa"
EndSection

```

The GPU is relatively new and drivers for it are in kernel 15.00. Which is why, after using that kernel in 20.04 successfully with one monitor to play the game Satisfactory, I updated to 21.04 and hoped I could begin to use two monitors.

It may be that the lack of settings in the file account for the  problems. I ask if, without causing more problems, I could backup the  existing file and remake it following the guide?

This is my system information:

```

makem@makems-TUF:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 21.04
Release:    21.04
Codename:    hirsute
makem@makems-TUF:~$ update-pciids
/usr/share/misc/pci.ids is read-only, exiting.
makem@makems-TUF:~$ sudo update-pciids
[sudo] password for makem: 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  272k  100  272k    0     0   847k      0 --:--:-- --:--:-- --:--:--  845k
Done.
makem@makems-TUF:~$ lspci | grep -i --color 'vga\|3d\|2d'
00:02.0 VGA compatible controller: Intel Corporation RocketLake-S GT1 [UHD Graphics 750] (rev 04)
00:17.0 SATA controller: Intel Corporation Device 43d2 (rev 11)
makem@makems-TUF:~$ sudo lspci -v -s 00:17.0
00:17.0 SATA controller: Intel Corporation Device 43d2 (rev 11) (prog-if 01 [AHCI 1.0])
    DeviceName: Onboard - SATA
    Subsystem: ASUSTeK Computer Inc. Device 8694
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 126
    Memory at a1500000 (32-bit, non-prefetchable) [size=8K]
    Memory at a1503000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 4090 [size=8]
    I/O ports at 4080 [size=4]
    I/O ports at 4060 [size=32]
    Memory at a1502000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci
makem@makems-TUF:~$

```

Monitor 1:

MSI Optix G241 Esports Gaming IPS Monitor

2x HDMI (1.4b)
1x Display Port (1.2a)

This monitor is attached to the Display Port

Monitor 2:

ASUS VS248HR

Signal Input : HDMI, D-Sub, DVI-D 
AV Audio Input : HDMI

This monitor is attached to the HDMI port

---

### Post by deadflowr on 2021-10-29
You probably wanted to run
```
lspci -v -s 00:02.0
```
instead of
```
lspci -v -s 00:17.0
```
Since the 00:17.0 relates to your hard drive controller.

(The lspci grep vga/3d/2d command outputted results for the sata controoler because it's id is 43d2, which contains 3d in the middle.)

Not that any if this is of any actual help.....

---

### Post by makem2 on 2021-10-29
> **deadflowr said:**
> You probably wanted to run
```
lspci -v -s 00:02.0
```
instead of
```
lspci -v -s 00:17.0
```
Since the 00:17.0 relates to your hard drive controller.

(The lspci grep vga/3d/2d command outputted results for the sata controoler because it's id is 43d2, which contains 3d in the middle.)

Not that any if this is of any actual help.....

Yes, I chose the wrong entry.

```

makem@makems-TUF:~$ lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation RocketLake-S GT1 [UHD Graphics 750] (rev 04) (prog-if 00 [VGA controller])
    DeviceName: Onboard - Video
    Subsystem: ASUSTeK Computer Inc. Device 8694
    Flags: bus master, fast devsel, latency 0, IRQ 159
    Memory at 6000000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 4000000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

makem@makems-TUF:~$

```

---

