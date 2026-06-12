---
title: "Dell Latitude D420 -&gt; internal GSM/UMTS Modem"
date: 2009-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by map84 on 2009-07-19
Hello,

my D420 has a built-in Modem with UMTS Support. I installed my SIM-Card, but couldn't find out, how to connect to the internet using the internal Modem. Either Network-Manager nor wicd couldn't detect the Device.

```

map@mp1:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Bus 004 is my external USB-Modem.

```

map@mp1:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

Does anybody know how to configure the Laptop's internal Modem?

Thank in advance!

---

### Post by map84 on 2009-09-09
I figured out, that i have to buy the WWAN-Card from Dell separetly, because it isn't supplied by default with this subnotebook.

---

### Post by Xianath on 2009-12-17
I'm in the same situation and would appreciate if you could share whether the add-on card from Dell worked or not. I'm pulling my hair out with the USB 3G modem that the company provided and might want to ask for a built-in card instead, if it works.

Thanks,
Peter

---

### Post by m666 on 2012-10-04
Bought on ebay:


[http://www.ebay.co.uk/itm/170915007658;jsessionid=1C788AB0A47F17B2C85FC087777DEDC9?ru=http%3A%2F%2Fwww.ebay.co.uk%2Fsch%2Fi.html%3F_sacat%3D0%26_from%3DR40%26_nkw%3D170915007658%26_rdc%3D1#ht_500wt_1124]("http://www.ebay.co.uk/itm/170915007658;jsessionid=1C788AB0A47F17B2C85FC087777DEDC9?ru=http%3A%2F%2Fwww.ebay.co.uk%2Fsch%2Fi.html%3F_sacat%3D0%26_from%3DR40%26_nkw%3D170915007658%26_rdc%3D1#ht_500wt_1124")


```
m@Dell:~$ lsusb 
Bus 001 Device 004: ID 0930:1302 Toshiba Corp. Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port
```

Works out of the box! Stronger signal than through mobile phone.
(I run Debian Wheezy)

---

