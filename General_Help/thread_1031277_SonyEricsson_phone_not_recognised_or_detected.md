---
title: "SonyEricsson phone not recognised or detected"
date: 2009-01-05
forum: General Help
---

### Post by t94xr on 2009-01-05
I have a SonyEricsson z710i 
my laptop has a bluetooth wireless card, using bluetooth disables wireless and wireless disables bluetooth but that isnt the issue.

I use a usb cable - cable tested to work on other systems and works fine but when i plug it into my ubuntu laptop on a working usb port and set the phone to either USB (flash stick) mode or phone mode, the phone isnt recognised or detected by the system.

Im not quite sure about it and i've tested it extensively, can anyone help?
:D

---

### Post by jim_p on 2009-01-05
> ... using bluetooth disables wireless and wireless disables bluetooth but that isnt the issue...

Blame network manager for that, and replace it with a better app.

About the phone. 
Is it identified in lsusb? 
```
lsusb
```
Do you get any weird messages in dmesg when you plug it in?
```
dmesg | tail
```

---

### Post by t94xr on 2009-01-05
Phone Mode:
```
t94xr@laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

t94xr@laptop:~$ dmesg | tail
[   29.642015] Bluetooth: RFCOMM ver 1.10
[   33.768761] eth0: link down
[   33.769415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.833116] [fglrx] GART Table is not in FRAME_BUFFER range 
[   33.841070] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   33.841094] [fgl[CODE]
```rx] Reserved FB block: Unshared offset:3ff5000, size:b000 
[   33.880532] NET: Registered protocol family 17
[   44.528036] ath0: no IPv6 routers present
[   72.668806] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  314.893725] process `skype' is using obsolete setsockopt SO_BSDCOMPAT[/CODE]

USB Mode (flash stick mode)
```
t94xr@laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

t94xr@laptop:~$ dmesg | tail
[   29.642015] Bluetooth: RFCOMM ver 1.10
[   33.768761] eth0: link down
[   33.769415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.833116] [fglrx] GART Table is not in FRAME_BUFFER range 
[   33.841070] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   33.841094] [fglrx] Reserved FB block: Unshared offset:3ff5000, size:b000 
[   33.880532] NET: Registered protocol family 17
[   44.528036] ath0: no IPv6 routers present
[   72.668806] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  314.893725] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```

helpful?

Any recommendations on a better network manager?

---

### Post by jim_p on 2009-01-05
Does the usb storage stick work when its plugged in that usb port?

Neither the usb storage stick, nor the phone plug in have even the tiniest effect in dmesg, so it may be a usb port not working issue.

This is what mine says for my k750:
dmesg
```
[ 4857.283613] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 4857.469190] usb 5-1: configuration #1 chosen from 1 choice
[ 4857.508131] usb 5-1: New USB device found, idVendor=0fce, idProduct=d016
[ 4857.508137] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4857.508140] usb 5-1: Product: Sony Ericsson K750
[ 4857.508142] usb 5-1: Manufacturer: Sony Ericsson
[ 4857.508144] usb 5-1: SerialNumber: 357849005132757_0
[ 4857.618818] cdc_acm 5-1:1.1: ttyACM0: USB ACM device
[ 4857.628793] cdc_acm 5-1:1.3: ttyACM1: USB ACM device
[ 4857.637266] usbcore: registered new interface driver cdc_acm
[ 4857.637273] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 4857.817593] Initializing USB Mass Storage driver...
[ 4857.817593] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4857.817593] usbcore: registered new interface driver usb-storage
[ 4857.817593] USB Mass Storage support registered.
[ 4857.827331] usb-storage: device found at 2
[ 4857.827337] usb-storage: waiting for device to settle before scanning
[ 4863.025980] usb-storage: device scan complete
[ 4863.028927] scsi 6:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[ 4863.038978] sd 6:0:0:0: [sdb] 124416 512-byte hardware sectors (64 MB)
[ 4863.044987] sd 6:0:0:0: [sdb] Write Protect is off
[ 4863.044991] sd 6:0:0:0: [sdb] Mode Sense: 00 6a 00 00
[ 4863.044994] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4863.054346] sd 6:0:0:0: [sdb] 124416 512-byte hardware sectors (64 MB)
[ 4863.060561] sd 6:0:0:0: [sdb] Write Protect is off
[ 4863.060566] sd 6:0:0:0: [sdb] Mode Sense: 00 6a 00 00
[ 4863.060569] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4863.060572]  sdb: sdb1
[ 4863.105471] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

lsusb
```
Bus 005 Device 002: ID 0fce:d016 Sony Ericsson Mobile Communications AB K750i Phone
```

For your wireless needs i suggest these
1) Network-config
Simple as it can get, lightweight and with an "extra layer" for administering networks, thus does not require root priviledges to configure.
Available through apt-get install.
[http://packages.ubuntu.com/intrepid/network-config](http://packages.ubuntu.com/intrepid/network-config)

2) Wicd
A bit more resource hungry than the above, also acts as an "extra layer" of administration.
Available here [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

3) Gnome-network-admin
My personal favorite. A bit hard if you don't know the networks ssid as it cannot scan, but it is not an "extra layer" again. It writes directrly in /etc/network/interfaces thus it needs root priviledges to configure.
Available through apt-get install.
[http://packages.ubuntu.com/intrepid/gnome-network-admin](http://packages.ubuntu.com/intrepid/gnome-network-admin)

4) Wifi-radar
I have not tested this one, so I can't give an opinion.
Available through apt-get install.
[http://packages.ubuntu.com/intrepid/wifi-radar](http://packages.ubuntu.com/intrepid/wifi-radar)

---

### Post by t94xr on 2009-01-05
yeah, it works in vista, same cable and all

ubuntu doesnt want to know about it, i have used other usb devices on this port and they have worked with no issues previously.

---

