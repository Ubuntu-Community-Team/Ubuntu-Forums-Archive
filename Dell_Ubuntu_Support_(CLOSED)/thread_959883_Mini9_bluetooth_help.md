---
title: "Mini9 bluetooth help"
date: 2008-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sleepercivic88 on 2008-10-26
I got a mini 9 about a week ago and with xp installed only becasue it was a shorter lead time for the xp installation.  I did a fresh install using a usb key of intrepid beta and got everything working except for the bluetooth.

lsmod | grep bluetooth

bluetooth    61924 6 rfcomm,sco,bnep,l2cap

hciconfig -a dosent return anything.  

my lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and  dmesg | grep Bluetooth
[   27.253557] Bluetooth: Core ver 2.13
[   27.254512] Bluetooth: HCI device and connection manager initialized
[   27.254521] Bluetooth: HCI socket layer initialized
[   27.282474] Bluetooth: L2CAP ver 2.11
[   27.282486] Bluetooth: L2CAP socket layer initialized
[   27.304608] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.304629] Bluetooth: BNEP filters: protocol multicast
[   27.375927] Bluetooth: SCO (Voice Link) ver 0.6
[   27.375946] Bluetooth: SCO socket layer initialized
[   27.413888] Bluetooth: RFCOMM socket layer initialized
[   27.413928] Bluetooth: RFCOMM TTY layer initial

Any recomendations on how to get this working.  It seems some people have had no problems.  Well, thanks in advanced.

---

### Post by superm1 on 2008-10-27
> **sleepercivic88 said:**
> I got a mini 9 about a week ago and with xp installed only becasue it was a shorter lead time for the xp installation.  I did a fresh install using a usb key of intrepid beta and got everything working except for the bluetooth.

lsmod | grep bluetooth

bluetooth    61924 6 rfcomm,sco,bnep,l2cap

hciconfig -a dosent return anything.  

my lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and  dmesg | grep Bluetooth
[   27.253557] Bluetooth: Core ver 2.13
[   27.254512] Bluetooth: HCI device and connection manager initialized
[   27.254521] Bluetooth: HCI socket layer initialized
[   27.282474] Bluetooth: L2CAP ver 2.11
[   27.282486] Bluetooth: L2CAP socket layer initialized
[   27.304608] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.304629] Bluetooth: BNEP filters: protocol multicast
[   27.375927] Bluetooth: SCO (Voice Link) ver 0.6
[   27.375946] Bluetooth: SCO socket layer initialized
[   27.413888] Bluetooth: RFCOMM socket layer initialized
[   27.413928] Bluetooth: RFCOMM TTY layer initial

Any recomendations on how to get this working.  It seems some people have had no problems.  Well, thanks in advanced.
At this point you will be better off grabbing the recovery ISO for the Mini9 OS from the posted support.dell.com link and installing from that there is custom support in it for enabling BT via the hotkey. I don't believe this has been ported to intrepid.

---

### Post by sleepercivic88 on 2008-10-27
> **superm1 said:**
> At this point you will be better off grabbing the recovery ISO for the Mini9 OS from the posted support.dell.com link and installing from that there is custom support in it for enabling BT via the hotkey. I don't believe this has been ported to intrepid.

I checked in the terminal by

sudo dellWirelessCtl --bt 0

and this is what dellWirelessCtl - i says

Libsmbios version      : 2.0.3
dellWirelessCtl version: 0.3.0
Wireless Info:
	Hardware switch not supported
	WiFi Locator not supported
	Wireless Keyboard not supported
	NVRAM Size: 256 bytes
	NVRAM format version: 1

Radio Status for WLAN:
	WLAN supported
	WLAN not installed
	WLAN disabled
	Status Code: 2

Radio Status for Bluetooth:
	Bluetooth not supported
	Status Code: 3

Radio Status for WWAN:
	WWAN not supported
	Status Code: 3

Wireless Switch Configuration
	WLAN switch control on
	Bluetooth switch control off
	WWAN switch control off
	switch config not locked
	WiFi locator disabled
	WiFi Locator config not locked

BIOS Boot-time settings (new interface):
	Wireless_Switch_Cellular_Control_Enable: (NOT SUPPORTED)
	Wireless_Switch_Cellular_Control_Disable: (NOT SUPPORTED)
	Wireless_Switch_Bluetooth_Control_Enable: (NOT SUPPORTED)
	Wireless_Switch_Bluetooth_Control_Disable: (NOT SUPPORTED)
	Wireless_Switch_Wireless_LAN_Control_Enable: (NOT SUPPORTED)
	Wireless_Switch_Wireless_LAN_Control_Disable: (NOT SUPPORTED)
	WiFi_Locator_Enable: (NOT SUPPORTED)
	WiFi_Locator_Disable: (NOT SUPPORTED)
	Cellular_Radio_Enable: (NOT SUPPORTED)
	Cellular_Radio_Disable: (NOT SUPPORTED)
	Bluetooth_Devices_Enable: (NOT SUPPORTED)
	Bluetooth_Devices_Disable: (NOT SUPPORTED)
	Wireless_LAN_Enable: 1
	Wireless_LAN_Disable: 0

BIOS Boot-time settings (old interface):
	Radio_Transmission_Enable: (NOT SUPPORTED)
	Radio_Transmission_Disable: (NOT SUPPORTED)
	Wireless_Device_Disable: 0
	Wireless_Device_App_Control: 0
	Wireless_Device_App_Or_Hotkey_Control: 1


could i just load the dell pa into my repos and install what I need. Im a bluetooth newbee so bare with me.  I cant load the usb_hci module eather

---

### Post by superm1 on 2008-10-27
> **sleepercivic88 said:**
> I checked in the terminal by

sudo dellWirelessCtl --bt 0

and this is what dellWirelessCtl - i says

Libsmbios version      : 2.0.3
dellWirelessCtl version: 0.3.0
Wireless Info:
    Hardware switch not supported
    WiFi Locator not supported
    Wireless Keyboard not supported
    NVRAM Size: 256 bytes
    NVRAM format version: 1

Radio Status for WLAN:
    WLAN supported
    WLAN not installed
    WLAN disabled
    Status Code: 2

Radio Status for Bluetooth:
    Bluetooth not supported
    Status Code: 3

Radio Status for WWAN:
    WWAN not supported
    Status Code: 3

Wireless Switch Configuration
    WLAN switch control on
    Bluetooth switch control off
    WWAN switch control off
    switch config not locked
    WiFi locator disabled
    WiFi Locator config not locked

BIOS Boot-time settings (new interface):
    Wireless_Switch_Cellular_Control_Enable: (NOT SUPPORTED)
    Wireless_Switch_Cellular_Control_Disable: (NOT SUPPORTED)
    Wireless_Switch_Bluetooth_Control_Enable: (NOT SUPPORTED)
    Wireless_Switch_Bluetooth_Control_Disable: (NOT SUPPORTED)
    Wireless_Switch_Wireless_LAN_Control_Enable: (NOT SUPPORTED)
    Wireless_Switch_Wireless_LAN_Control_Disable: (NOT SUPPORTED)
    WiFi_Locator_Enable: (NOT SUPPORTED)
    WiFi_Locator_Disable: (NOT SUPPORTED)
    Cellular_Radio_Enable: (NOT SUPPORTED)
    Cellular_Radio_Disable: (NOT SUPPORTED)
    Bluetooth_Devices_Enable: (NOT SUPPORTED)
    Bluetooth_Devices_Disable: (NOT SUPPORTED)
    Wireless_LAN_Enable: 1
    Wireless_LAN_Disable: 0

BIOS Boot-time settings (old interface):
    Radio_Transmission_Enable: (NOT SUPPORTED)
    Radio_Transmission_Disable: (NOT SUPPORTED)
    Wireless_Device_Disable: 0
    Wireless_Device_App_Control: 0
    Wireless_Device_App_Or_Hotkey_Control: 1


could i just load the dell pa into my repos and install what I need. Im a bluetooth newbee so bare with me.  I cant load the usb_hci module eather
Unfortunately dellWirelessCtl can't control the BT on these devices.

---

### Post by sleepercivic88 on 2008-11-05
I got the bluetooth working today and im pretty happy.  I went to the dell repo and downloaded the aircraft-manager package and enabled bluetooth power and now everything works.  So I guess my problems are solved.

---

### Post by aldrydd on 2008-11-06
> **sleepercivic88 said:**
> I got the bluetooth working today and im pretty happy.  I went to the dell repo and downloaded the aircraft-manager package and enabled bluetooth power and now everything works.  So I guess my problems are solved.

I'm a complete Linux/Ubuntu newbie, but seem to be having the same issue as yourself with the Mini 9's Bluetooth.

"I went to the dell repo and downloaded the aircraft-manager package" sounds kinda like a foreign language to me... Is there any way you could tell me what this means or how I could give it a shot?

---

