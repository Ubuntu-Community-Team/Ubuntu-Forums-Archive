---
title: "Inspiron 1525 + Karmic 9.10 + Bluetooth"
date: 2009-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eidaot on 2009-11-06
I'm running on a Dell Inspiron 1525 using 9.10 Karmic 64bit.

I've just recently added on a Bluetooth BCM92045MD internal adapter.  
In the BIOS, bluetooth is set to on.  The wireless switch is set to control all (wireless and BT).  It detects on boot, dmesg shows that.  I've got my front panel still off, and I can unplug and plug up the adapter and /var/log/messages shows that the device is being removed and added.  However when I run ```
sudo hcitool dev
```I get no devices shown.

I know that hcitool work, because I have a D-Link USB DBT-120 that shows up and works perfectly.

```
sudo dellWirelessCtl --st_bt
```It shows it's enabled at boot, supported, enabled, controlled by wireless switch at boot, runtime switch control currently enabled.  However it also said "Bluetooth not installed".

I do bluetooth programming with python and am wondering what I am missing?  If you guys need more information, I'll post actual results of dmesg, messages, dellWirelessCtl, and such.

Thanks for any suggestions on this!

---

### Post by eidaot on 2009-11-06
To add some detail to my previous message, here are some of my outputs.  Hopefully someone can point me in the right direction.

```
dmesg |grep tooth
[    0.430009] Bluetooth: Core ver 2.15
[    0.430023] Bluetooth: HCI device and connection manager initialized
[    0.430023] Bluetooth: HCI socket layer initialized
[    0.839285] Bluetooth: L2CAP ver 2.13
[    0.839287] Bluetooth: L2CAP socket layer initialized
[    0.839290] Bluetooth: SCO (Voice Link) ver 0.6
[    0.839292] Bluetooth: SCO socket layer initialized
[    0.839327] Bluetooth: RFCOMM TTY layer initialized
[    0.839330] Bluetooth: RFCOMM socket layer initialized
[    0.839332] Bluetooth: RFCOMM ver 1.11
```

hcitool show's nothing
```
sudo hcitool dev
Devices:
```

```
sudo dellWirelessCtl --st_bt

Radio Status for Bluetooth:
	Bluetooth enabled at boot
	Bluetooth supported
	Bluetooth enabled
	Bluetooth installed
	Bluetooth controlled by wireless switch at boot
	Bluetooth runtime switch control currently enabled
	Status Code: 0
```

Even running the bluetooth-agent manually shows that bluetooth is enabled.  I click on enable using the agent, the button goes disabled and it just waits and never comes back.
```
bluetooth-properties 
** Message: adding killswitch idx 1 state 1
** Message: Reading of RFKILL events failed
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: RFKILL event: idx 1 type 2 op 2 soft 0 hard 0
  <I click on Enable Bluetooth in the progrma>
** Message: killswitch 1 is 1
** Message: killswitches state 1
```

Interesting enough, lsusb shows up the broadcom usb devices as a keyboard and mouse?!  Very strange.
```
sudo lsusb -s7: -v

Bus 007 Device 007: ID 0a5c:4503 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x4503 
  bcdDevice            1.00
  iManufacturer           1 Broadcom Corp
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 71 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered

Bus 007 Device 006: ID 0a5c:4502 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x4502 
  bcdDevice            1.00
  iManufacturer           1 Broadcom Corp
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 36 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered

Bus 007 Device 005: ID 0a5c:4500 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x4500 
  bcdDevice            1.00
  iManufacturer           1 Broadcom
  iProduct                2 BCM2045B2
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x0e
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0103 power enable connect
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by groovomata on 2009-11-07
Hmmm, my bluetooth isn't working either. I checked the bios for my inspiron 6400 and it says that bluetooth is enabled. The function key F2 should also turn it on and off along with my wireless card, however the wireless icon is on, but the bluetooth one is not. As well, the gnome bluetooth app is showing "Bluetooth is Disabled". My question is, how do I turn it on?

---

### Post by TheHolm on 2009-11-08
I have similar problem with Dell XPS 16. I have seen a thread somewhere (and I fail to find this link now) that Vista driver updates Broadcom firmware wich makes it unaccesable from linux. 

There is a tool on Dell site to reflash old firmware to reanable it. 

May be it helps.

---

### Post by eidaot on 2009-11-08
[http://kerneltrap.org/mailarchive/linux-kernel/2008/3/7/1106944/thread#mid-1106944]("http://kerneltrap.org/mailarchive/linux-kernel/2008/3/7/1106944/thread#mid-1106944")

I found this link but for the life of me I don't understand how to use it.  I haven't compiled a kernel since slackware 2.0.  Anyone know if this would work for my case or if it's even relevant?

---

### Post by TheHolm on 2009-11-09
Problem seems lay in fact that Dell Bluetooth module does not have correct device info.  

 *bDeviceClass            9 Hub* does not sounds good.

> Bus 007 Device 005: ID 0a5c:4500 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8


Normal bluetooth dongle should has something like bellow

> Bus 003 Device 006: ID 0a5c:2039 Broadcom Corp.

Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth

---

### Post by groovomata on 2009-11-09
You wouldn't be able to post a link to that Dell firmware would you? I can't seem to find it.
Thank you,
Erik.

---

### Post by eidaot on 2009-11-20
[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714]("http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714")

Found it!  This firmware patch fixed my bluetooth and will now even work in Windows 7 (in case anyone cared.)

I'm giving credit to this other site I found regarding my model of Inspiron 1525 and his attempt to downgrade to XP.  He had the magic link to the Dell firmware patch.
[http://www.khanh.net/blog/archives/27-Installing-Windows-XP-on-a-Dell-Inspiron-1525-downgrading-from-Windows-Vista.html]("http://www.khanh.net/blog/archives/27-Installing-Windows-XP-on-a-Dell-Inspiron-1525-downgrading-from-Windows-Vista.html")

Thank you all for your help on this, you guys are a great community!

---

### Post by TheHolm on 2009-11-20
It works on my XPS 16. After installing driver under Window 7 I got Bluetooth in Ubuntu 9.10/64.

---

### Post by shadetree1 on 2009-12-10
Thanks for the link to the Dell Driver patch :) 
 
My first install with Karmic on a Dell Inspiron 1318 had me scratching my head for a while with this Bluetooth issue.
 
shadetree

---

