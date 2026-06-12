---
title: "Studio XPS 1340"
date: 2009-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by phndrummer on 2009-10-07
Hi all

I've been having some trouble finding the drivers for my studio xps laptop. I've spent several hours searching for them. Here is the hardware I need driver for.

 a Nvidia 9400M G gpu
 a 1515 wireless N adapter
 and a 370 bluetooth adapter

Oh, and the computer is 64bit. If someone could send me a link, or I'm fairly good with the terminal so if someone knew the commands, then that'd be great. Thanks.

--Phndrummer

---

### Post by c0mput3r_n3rD on 2009-10-07
Go to System -> Administration -> Hardware Drivers, and it will search for the right propriety software for your hardware, which should at least be for your video driver and wireless card

---

### Post by phndrummer on 2009-10-07
That only worked for the Nvidia driver, I cannot find any other place to update or find the drivers for the wireless and the bluetooth

---

### Post by EricDB on 2009-10-16
I'm running the Karmic beta on my new 1340.  For video I activated version 185 of the NVIDIA driver, and for wireless the Broadcom STA driver works great.  I'm not sure if my card is the 1515, but see if you get the same output from lspci:
```
$ lspci|grep Wireless
06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

Bluetooth is fine--I'm not sure whether it worked out of the box or after installing those drivers.  

Good luck!

---

### Post by Sephoroth on 2009-10-17
IIRC it is the Dell Wireless 1510 which is Broadcom (BCM4322) based and the 1515 is Atheros based.

---

### Post by neonum6 on 2009-11-09
Hi everybody! my bluetooth device does't work. this is my "dmesg | grep Bluetooth"
```
[    0.470005] Bluetooth: Core ver 2.15
[    0.470016] Bluetooth: HCI device and connection manager initialized
[    0.470016] Bluetooth: HCI socket layer initialized
[    0.949787] Bluetooth: L2CAP ver 2.13
[    0.949788] Bluetooth: L2CAP socket layer initialized
[    0.949791] Bluetooth: SCO (Voice Link) ver 0.6
[    0.949792] Bluetooth: SCO socket layer initialized
[    0.949812] Bluetooth: RFCOMM TTY layer initialized
[    0.949814] Bluetooth: RFCOMM socket layer initialized
[    0.949816] Bluetooth: RFCOMM ver 1.11

```
and this is my "sudo hcitool device"
```
Devices: 
```

what can I do?

---

### Post by TheHolm on 2009-11-09
> 
and this is my "sudo hcitool device"
```
Devices: 
```

what can I do?

sudo lsusb ? 

And ```
sudo lsusb -v -s x:x
```  - where x:x is address of you Broadcomm bluetooth.

---

### Post by neonum6 on 2009-11-09
here is lsusb
```
Bus 002 Device 002: ID 0c45:63fa Microdia 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

..why my system does not activate the Bluetooth automatically?

---

### Post by neonum6 on 2009-11-09
lsusb -s 003:002 just tells me:
```

Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 

```

---

### Post by TheHolm on 2009-11-09
> **neonum6 said:**
> here is lsusb
```

Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 

```

..why my system does not activate the Bluetooth automatically?

Could you please provide output for 
```

 sudo lsusb -v -s 3:2

```

---

### Post by neonum6 on 2009-11-09
this is the output of the command that you suggested me.

```
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
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
  iProduct                2 BCM2046B1
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
    MaxPower               94mA
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
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0001
  Self Powered

```

---

### Post by TheHolm on 2009-11-09
Ahhh. Welcome to club. We was broadcommed. 

I'm trying to find cure on it under 

[http://ubuntuforums.org/showthread.php?p=8277214]("http://ubuntuforums.org/showthread.php?p=8277214").

NO much luck so far. But at least problem is clear.

---

### Post by EricDB on 2009-11-09
Have you activated "Broadcom STA wireless driver" in the Hardware Drivers settings?  I have the same laptop with the same card, and mine worked after I did that.

**Edit:** Here is the output of "dmesg|grep Bluetooth" for my working system:
```
eric@eric-13:~/torch$ dmesg|grep Bluetooth
[    0.430006] Bluetooth: Core ver 2.15
[    0.430017] Bluetooth: HCI device and connection manager initialized
[    0.430017] Bluetooth: HCI socket layer initialized
[    0.839191] Bluetooth: L2CAP ver 2.13
[    0.839193] Bluetooth: L2CAP socket layer initialized
[    0.839195] Bluetooth: SCO (Voice Link) ver 0.6
[    0.839197] Bluetooth: SCO socket layer initialized
[    0.839229] Bluetooth: RFCOMM TTY layer initialized
[    0.839231] Bluetooth: RFCOMM socket layer initialized
[    0.839233] Bluetooth: RFCOMM ver 1.11
[   13.473468] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   16.674381] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.674383] Bluetooth: BNEP filters: protocol multicast
[   55.939443] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[20509.500356] input: Bluetooth Travel Mouse as /devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4.3/3-4.3:1.0/bluetooth/hci0/hci0:11/input18
[20509.500461] generic-bluetooth 0005:046D:B002.0004: input,hidraw1: BLUETOOTH HID v48.09 Mouse [Bluetooth Travel Mouse] on 00:22:5F:F7:8D:4A
```

---

### Post by neonum6 on 2009-11-09
> **EricDB said:**
> Have you activated "Broadcom STA wireless driver" in the Hardware Drivers settings?  I have the same laptop with the same card, and mine worked after I did that.

**Edit:** Here is the output of "dmesg|grep Bluetooth" for my working system:
```
eric@eric-13:~/torch$ dmesg|grep Bluetooth
[    0.430006] Bluetooth: Core ver 2.15
[    0.430017] Bluetooth: HCI device and connection manager initialized
[    0.430017] Bluetooth: HCI socket layer initialized
[    0.839191] Bluetooth: L2CAP ver 2.13
[    0.839193] Bluetooth: L2CAP socket layer initialized
[    0.839195] Bluetooth: SCO (Voice Link) ver 0.6
[    0.839197] Bluetooth: SCO socket layer initialized
[    0.839229] Bluetooth: RFCOMM TTY layer initialized
[    0.839231] Bluetooth: RFCOMM socket layer initialized
[    0.839233] Bluetooth: RFCOMM ver 1.11
[   13.473468] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   16.674381] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.674383] Bluetooth: BNEP filters: protocol multicast
[   55.939443] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[20509.500356] input: Bluetooth Travel Mouse as /devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4.3/3-4.3:1.0/bluetooth/hci0/hci0:11/input18
[20509.500461] generic-bluetooth 0005:046D:B002.0004: input,hidraw1: BLUETOOTH HID v48.09 Mouse [Bluetooth Travel Mouse] on 00:22:5F:F7:8D:4A
```

Is Hardware driver in the gnome panel? In that panel I don't have any broadcom voice..

---

### Post by neonum6 on 2009-11-12
it's amazing...but now it works!!! 
This is appened after installing drivers on seven 64bit...I don't know how...this is a very very strange...

---

### Post by Kareeser on 2010-04-16
It seems as though the installation of the bluetooth driver in Windows does the job of **turning on** the device.

So for our purposes, the actual bluetooth device is off, and there's no way to turn it on.

Short of re-installing Windows, there has to be a way to turn it on from Linux!

---

