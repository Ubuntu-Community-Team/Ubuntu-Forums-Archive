---
title: "Dell XPS 14 Bluetooth not working (10.10, 64bit)"
date: 2010-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tomei Ningen on 2010-12-27
Hello,

I have Dell XPS 14 laptop (L401X)

I have enabled bluetooth in the BIOS. When I log into ubuntu 10.10 64 bit and run the bluetooth-applet, it says:

Bluetooth is disabled.

There is a big button called "Turn On Bluetooth". When I press this button, the button just turns gray, and nothing happens.

I tried starting the bluetooth service manually, but it doesn't seem to show any effect:

~# /etc/init.d/bluetooth start
~# /etc/init.d/bluetooth status
 * bluetooth is not running

lsusb show nothing (I am not sure if my bluetooth device is supposed to be shown here)

~# lsusb
Bus 002 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 002 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0408:2fb2 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried to start the bluetoothd manually:

~# bluetoothd 
~# tail /var/log/daemon.log
Dec 27 00:36:21 deli bluetoothd[2744]: Bluetooth deamon 4.69
Dec 27 00:36:21 deli bluetoothd[2744]: Starting SDP server
Dec 27 00:36:21 deli bluetoothd[2744]: Starting experimental netlink support
Dec 27 00:36:21 deli bluetoothd[2744]: Failed to find Bluetooth netlink family
Dec 27 00:36:21 deli bluetoothd[2744]: Failed to init netlink plugin

But anyway there seems to be something related to bluetooth discovered by the kernel (right at the end of dmesg, so I think the logs were triggered when I ran bluetoothd manually)

~# dmesg | grep -n -i blue
863:[  600.925002] Bluetooth: Core ver 2.15
865:[  600.925018] Bluetooth: HCI device and connection manager initialized
866:[  600.925020] Bluetooth: HCI socket layer initialized
867:[  600.930175] Bluetooth: L2CAP ver 2.14
868:[  600.930180] Bluetooth: L2CAP socket layer initialized
869:[  600.964772] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
870:[  600.964777] Bluetooth: BNEP filters: protocol multicast
871:[  600.978534] Bluetooth: SCO (Voice Link) ver 0.6
872:[  600.978539] Bluetooth: SCO socket layer initialized
~# dmesg | wc
    872    7487   57939

Any clues?

---

### Post by pedi0022003 on 2010-12-31
actually I have the same problem.but when i run lsusb i get this:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
[COLOR="DarkRed"]***Bus 005 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II***[/COLOR]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
and if i run "rfkill list" I get this:
```

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
so this show i HAVE a bluetooth device but i dont know why its not working!any help?

---

### Post by Tomei Ningen on 2011-01-01
I will probably just go buy a bluetooth dongle and be done with this mess :-)

---

### Post by anushcbe on 2012-01-07
Bluetooth is working with Ubuntu 11.10. (X64)
Try it out

---

