---
title: "Slow USB transfer"
date: 2011-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Benic on 2011-01-31
After upgrading to 10.10, USB transfer speed is painfully slow. It looks like USB 2.0 is not supported, although it is detected. I'm using a pcmcia usb 2.0 hub  and speed was normal with 9.10 or 10.04. It's not like bug [_197762_]("https://bugs.launchpad.net/ubuntu/+bug/197762?comments=all") as speed is always slow for all files, no matter how big it is. I had to set acpi=off in grub to prevent the pcmcia hub to crash. Turning it on doesn't make a difference.

```
portable@portable1:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
```

```
portable@portable1:~$ dmesg | grep usb
[    0.073267] usbcore: registered new interface driver usbfs
[    0.073348] usbcore: registered new interface driver hub
[    0.073450] usbcore: registered new device driver usb
[    0.597821] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.517024] usbcore: registered new interface driver hiddev
[    1.530669] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[    1.531173] generic-usb 0003:046D:C03D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[    1.531669] usbcore: registered new interface driver usbhid
[    1.531732] usbhid: USB HID core driver
[ 4477.673851] usb 5-1: new high speed USB device using ehci_hcd and address 2
[ 4478.077837] usb 5-1.1: new high speed USB device using ehci_hcd and address 3
[ 4478.257954] usb 5-1.3: new high speed USB device using ehci_hcd and address 4
[ 4478.295852] scsi2 : usb-storage 5-1.1:1.0
[ 4478.298533] usbcore: registered new interface driver usb-storage
[ 4478.391979] scsi3 : usb-storage 5-1.3:1.0
[ 4485.718522] usb 5-1.1: USB disconnect, address 3
[ 4505.857829] usb 5-1.1: new high speed USB device using ehci_hcd and address 5
[ 4505.976047] scsi4 : usb-storage 5-1.1:1.0
```

---

