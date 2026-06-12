---
title: "Bluetooth not working / Latitude E5420"
date: 2011-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by snowguy on 2011-10-30
i have a new latitude E5420. I bought it with Windows 7 but I installed ubuntu 11.10 32 bit as dual boot. I can get the bluetooth to work in windows 7 fine but I can't get past the "searching for devices" part to pair it when in ubuntu. It never finds anything. I have tried this with a pair of bluetooth headphones and a bluetooth speaker. And I did ensure that each was in pairing mode right next to the computer. All of this leads me to believe it is some ubuntu software issue. But I'm surprised that I can't find anyone else that seems to have quite the same problem I am having.

Any suggestions on what to try? 

Here's some additional info, running some command line things I saw requested on other bluetooth related issue posts.

```

dmesg |grep -i bluetooth
[    4.473211] Bluetooth: Core ver 2.16
[    4.474054] Bluetooth: HCI device and connection manager initialized
[    4.474056] Bluetooth: HCI socket layer initialized
[    4.474058] Bluetooth: L2CAP socket layer initialized
[    4.475050] Bluetooth: SCO socket layer initialized
[    4.485033] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    4.966908] Bluetooth: RFCOMM TTY layer initialized
[    4.966913] Bluetooth: RFCOMM socket layer initialized
[    4.966915] Bluetooth: RFCOMM ver 1.11
[    4.968914] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.968916] Bluetooth: BNEP filters: protocol multicast

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05ca:181e Ricoh Co., Ltd 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver


sudo hcitool dev
Devices: [nothing is listed]

sudo rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by snowguy on 2012-02-15
Just want to let anyone else know who has had the same issue that I tried again today and things are working. I assume an update has come through in the last while which resolves this problem.

---

### Post by kghunt on 2012-03-05
I have an E5420. Do you get issues with slow downs while charging? (if the battery is not full) ?

---

### Post by snowguy on 2012-03-06
I only use my battery about every other week. I typically leave it at 40% charged disconnected from my laptop in order to preserve the battery. So I may not be the best person to ask. But in any case, I do charge it occasionally and have never noticed a slowdown.

---

