---
title: "Useless Mini9 with ubuntu - No wireless connection...again"
date: 2009-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Shadefly on 2009-06-14
1

---

### Post by pastalavista on 2009-06-14
If you don't want your Mini any more, I'll gladly take it off your hands. There are Linux wireless drivers for it. If you want help, you should ask.

---

### Post by Shadefly on 2009-06-14
I had this issue back in april and posted the issue. I got help, but no reolution. I ended up reloading the os to get connected to my secure wireless network again. Then went on vacation. I created a travel profile so the secure network settings would not get corrupted. It recognized wireless networks at hotels and campground fine. When I returned, changed to the home profile, no wireless connectivity at all. In fact it does not even recognize the wireless card any more.

here are results of nm-tool:
NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            r8169
  Active:            yes
  HW Address:        00:24:E8:96:25:77

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings
    Hardware Link:   yes

  IP Settings:
    IP Address:      192.168.1.10
    Subnet Mask:     255.255.255.0
    Broadcast:       192.168.1.255
    Gateway:         192.168.1.1
    Primary DNS:     192.168.1.1
    Secondary DNS:   0.0.0.0

It is using the wl driver when i check in administration/hardwaredrivers

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:71:3d:4a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.5 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:96:25:77
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.10 latency=0 module=r8169 multicast=yes

how can i get this thing to connect to my secure network at home, travel and not have to reload the os the connect to the secure network again?

---

### Post by ugm6hr on 2009-06-15
Which version of Ubuntu?  Default 8.04 or 9.04NBR?

I found the wifi control in 8.04 a little less than satisfactory, but never had these issues.

---

### Post by Shadefly on 2009-06-15
I was using 8.04.1. Last night I loaded 9.04 Jaunty Jackalope and was able to get it connected to my wireless network (using WEP) after configuring it 3 or 4 times. We wont be traveling for a couple more weeks but I may take it with me out of town this week as a test.

9.04 seems much more stable, boots faster, and seems to have better wireless management. I like the GUI better also. I'll post again later this week.

---

