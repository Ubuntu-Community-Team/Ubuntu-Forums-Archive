---
title: "wifi on a &quot;acer travelmate 2700&quot;"
date: 2005-11-12
forum: Desktop Environments
---

### Post by tipi on 2005-11-12
hi there,
i'm looking for a solution to get the wifi on my notebook up and running
it's an acer travelmate 2700
installed almost every suitable driver i could find trough ndiswrapper...
this is what i see   (see attachments 123)

1
in the wireless network drivers window:neti2220 driver is marked as installed
however, hardware is not detected??? this is the original driver from the acer
site.

2
in the system information window you can see that under pci devices
a linksys improcomm ipn 2220 wireless lan adapter is recognized???

3
in the window networksettings no wlan device or connection can be found??

my conclusion is, the driver is installed, the device recognized and still
it does not work :(  
help

---

### Post by Lambert on 2005-11-12
Can you run this

```
sudo lshw -C network
```

and print the output here.

---

### Post by tipi on 2005-11-13
here it comes

thijs@ubuntutut:~$ sudo lshw -C network
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 2
       bus info: pci@02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:a400-a41f iomemory:d0200800-d020081f iomemory:d0200000-d02007ff irq:11
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:09:47:d1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.4 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:d0200c00-d0200cff irq:19
thijs@ubuntutut:~$

---

### Post by tipi on 2005-11-13
and maybe it's important to mention that there is a on/off button for wifi on the 
notebook,

---

### Post by Lambert on 2005-11-13
I found [COLOR=Blue][this]("http://ubuntuforums.org/archive/index.php/t-34934.html")[/COLOR] post which looks like they had the same problem as you. If you have the driver installed, uninstall it and start over. Copy all the files from the driver folder (.dll; .sys) of the cd into a folder on your drive. Then go through the steps of installing the drive again and see if that solves it.

---

### Post by tipi on 2005-11-13
great, i'l try this tonight and let you know how it went
thx

---

### Post by tipi on 2005-11-13
yipee
driver oke,hardware oke,wireless working and internet connection up:)
again, thx for your help lambert
greetz from Be.

---

