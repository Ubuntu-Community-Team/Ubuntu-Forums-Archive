---
title: "Phone no longer detected by ubuntu 9.04"
date: 2009-06-19
forum: General Help
---

### Post by tkdryan on 2009-06-19
There seems to be a new problem with 9.04, it won't automatically detect my phone's storage when plugged in via USB. My phone is a Moto ROKR Z6. Laptop is Dell Latitude c800.

This worked fine in 8.04 and 8.10. Recently upgraded to 9.04 and now the phone only charges when plugged in, it won't mount the 2GB Micro SD card. I have downloaded and installed all updates for 9.04.

lspci output:
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

sudo fdisk -l output:
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8abb8abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2675     1951897+  82  Linux swap / Solaris
/dev/sda3            2676        4864    17583142+   5  Extended
/dev/sda5            2676        3648     7815591   83  Linux
/dev/sda6            3649        4864     9767488+  83  Linux
(multiple instllations on disk)

uname -a
Linux ubuntop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

I know there is nothing wrong with any of the hardware as everything works still on another machine running XP, and even the same machine running ubuntu 8.04 (i have multiple versions installed here). The kernel on my 8.04 install is 2.6.24-16-generic

I am not a linux expert by any means, but I will do my best to check for suggestions frequently as I know I am not the only one with this problem. I have seen other posts here with no resolution.

Any help or suggestions will be greatly appreciated. I only ask that if you suggest having me run some command in attempt to fix this issue, please include a corresponding command to set things back in case it does not resolve the issue.

Thanks!!!

---

### Post by Gunman1982 on 2009-06-19
When the phone is plugged in via usb execute 'dmesg | tail' and 'lsusb' in the terminal to give some more info please.

---

### Post by tkdryan on 2009-06-19
lsusb output:
Bus 001 Device 003: ID 05c6:1000 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | tail output:
[   42.986658] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.816080] wlan0: no IPv6 routers present
[  210.424090] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  210.488132] hub 1-0:1.0: unable to enumerate USB device on port 1
[  212.208075] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  212.372478] usb 1-1: configuration #1 chosen from 1 choice
[  212.868647] Initializing USB Mass Storage driver...
[  212.876221] usb-storage: probe of 1-1:1.0 failed with error -5
[  212.876319] usbcore: registered new interface driver usb-storage
[  212.876331] USB Mass Storage support registered.

Thank you.

---

### Post by tkdryan on 2009-06-19
Tried the quick fix for a similar issue where ubuntu 9.04 does not recognize cameras by running:

sudo killall gvfs-gphoto2-volume-monitor

then hooking up the phone and it still doesn't work. dmesg gives the same output.

---

### Post by tkdryan on 2009-06-19
Maybe this is caused by ext4, which I am trying with this 9.04 installation. I will try a seperate install with 9.04 and ext3 on the same machine to see if I have any errors and I will post back. Any feedback is appreciated....

---

### Post by tkdryan on 2009-06-20
I treid 9.04 on ext3 on the same machine, and I am running in to the same problem. Something changed from 8.10 to 9.04. . .

---

