---
title: "Bluetooth devices are not found and the adapter can not be found"
date: 2017-04-13
forum: Debian
---

### Post by fredward on 2017-04-13
I tried almost everything I found in this and other forum to get my Bluetooth device on my laptop working.
It's definitely a problem of Gnu/Linux because in Windows Bluetooth is working without any problems.
Also other devices found each other. But no device found my Computer and my Computer doesn't find any devices.
My Bluetooth is set to always discoverable.

[B]hcitool dev
[/B]```
Devices:
    hci0    54:27:1E:93:A4:D2
```

[B]sudo service bluetooth status
[/B]```
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled)
   Active: active (running) since Thu 2017-04-13 14:42:58 CEST; 57min ago
     Docs: man:bluetoothd(8)
 Main PID: 880 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;880 /usr/lib/bluetooth/bluetoothd

Apr 13 14:42:58 Oberst bluetoothd[880]: Bluetooth daemon 5.23
Apr 13 14:42:58 Oberst systemd[1]: Started Bluetooth service.
Apr 13 14:42:58 Oberst bluetoothd[880]: Starting SDP server
Apr 13 14:42:58 Oberst bluetoothd[880]: Bluetooth management interface 1.6 initialized
Apr 13 14:42:58 Oberst bluetoothd[880]: Sap driver initialization failed.
Apr 13 14:42:58 Oberst bluetoothd[880]: sap-server: Operation not permitted (1)
Apr 13 14:42:58 Oberst bluetoothd[880]: hci0 Load Connection Parameters failed: Unknown Command (0x01)

```

[B]lspci -nnk | grep -iA2 net
[/B]```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:3501]
    Kernel driver in use: r8169

```

[B]sudo rfkill list
[/B]```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

[B]uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
[/B]```
Linux Oberst 3.16.0-4-amd64 #1 SMP Debian 3.16.39-1+deb8u2 (2017-03-07) x86_64 GNU/Linux
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:3501]
    Kernel driver in use: r8169
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 5986:055f Acer, Inc 
Bus 003 Device 004: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 041e:3233 Creative Technology, Ltd 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.758581] usb 3-7: Product: Bluetooth Radio 
[    3.146109] Bluetooth: Core ver 2.19
[    3.146120] Bluetooth: HCI device and connection manager initialized
[    3.146126] Bluetooth: HCI socket layer initialized
[    3.146127] Bluetooth: L2CAP socket layer initialized
[    3.508923] Bluetooth: SCO socket layer initialized
[    3.630819] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.630820] Bluetooth: BNEP filters: protocol multicast
[    3.630826] Bluetooth: BNEP socket layer initialized
[   14.636093] Bluetooth: RFCOMM TTY layer initialized
[   14.636102] Bluetooth: RFCOMM socket layer initialized
[   14.636106] Bluetooth: RFCOMM ver 1.11
[    0.239849] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.795731] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    2.798171] rtl8723be 0000:03:00.0: firmware: direct-loading firmware rtlwifi/rtl8723befw.bin
[    3.014265] r8169 0000:04:00.1: firmware: direct-loading firmware rtl_nic/rtl8411-2.fw
[    4.116543] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    4.367464] nouveau  [  PGRAPH][0000:01:00.0] using external firmware
[    4.367474] nouveau 0000:01:00.0: firmware: failed to load nouveau/nv117_fuc409c (-2)
[    4.367493] nouveau 0000:01:00.0: Direct firmware load failed with error -2
[    4.367766] nouveau 0000:01:00.0: firmware: failed to load nouveau/fuc409c (-2)
[    4.367783] nouveau 0000:01:00.0: Direct firmware load failed with error -2
bluetooth             374429  30 bnep,btusb,rfcomm
6lowpan_iphc           16588  1 bluetooth
rfkill                 18867  4 cfg80211,bluetooth
crc16                  12343  2 ext4,bluetooth

```

[B]lsusb
[/B]```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 5986:055f Acer, Inc 
Bus 003 Device 004: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 041e:3233 Creative Technology, Ltd 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[B]sudo cat /sys/kernel/debug/usb/devices
[/B]```
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev= 3.16
S:  Manufacturer=Linux 3.16.0-4-amd64 xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh=14
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  7
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.16
S:  Manufacturer=Linux 3.16.0-4-amd64 xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.03
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=8ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=2ms
I:* If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=  32 Ivl=2ms

T:  Bus=03 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=3233 Rev= 2.28
S:  Manufacturer=Creative Technology Ltd
S:  Product=Sound Blaster X-Fi Go! Pro
S:  SerialNumber=00327630
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=120mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 1 #EPs= 2 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=05(Isoc) MxPS= 200 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   3 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=05(Isoc) MxPS= 300 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   3 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=81(I) Atr=05(Isoc) MxPS= 200 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=84(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

T:  Bus=03 Lev=01 Prnt=01 Port=06 Cnt=03 Dev#=  4 Spd=12   MxCh= 0
D:  Ver= 2.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b002 Rev= 2.00
S:  Manufacturer=Realtek 
S:  Product=Bluetooth Radio 
S:  SerialNumber=00e04c000001
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms

T:  Bus=03 Lev=01 Prnt=01 Port=07 Cnt=04 Dev#=  5 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=055f Rev= 6.05
S:  Manufacturer=Generic
S:  Product=BisonCam, NB Pro
S:  SerialNumber=200901010001
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
A:  FirstIf#= 0 IfCount= 2 Cls=0e(video) Sub=03 Prot=00
I:* If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=4ms
I:* If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 128 Ivl=125us
I:  If#= 1 Alt= 2 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 512 Ivl=125us
I:  If#= 1 Alt= 3 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1024 Ivl=125us
I:  If#= 1 Alt= 4 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1536 Ivl=125us
I:  If#= 1 Alt= 5 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2048 Ivl=125us
I:  If#= 1 Alt= 6 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2688 Ivl=125us
I:  If#= 1 Alt= 7 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=3072 Ivl=125us

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 2
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.16
S:  Manufacturer=Linux 3.16.0-4-amd64 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480  MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev= 0.05
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 2
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.16
S:  Manufacturer=Linux 3.16.0-4-amd64 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480  MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev= 0.05
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

```

---

### Post by fredward on 2017-04-13
I solved the problem with this tutorial:
[https://iamjagjeetubhi.wordpress.com/2016/06/19/install-realtek-rtl8723be-wifi-drivers-in-arch-linux/](https://iamjagjeetubhi.wordpress.com/2016/06/19/install-realtek-rtl8723be-wifi-drivers-in-arch-linux/)

You need this: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) to work.
Maybe it can help someone with the same problem.

---

### Post by jeremy31 on 2017-04-13
*Thread moved to **Debian**.*

It might work in Ubuntu 16.04 as support for Realtek Bluetooth was added in the 4.0+ kernels and it appears you are using a 3.16 Debian kernel

---

