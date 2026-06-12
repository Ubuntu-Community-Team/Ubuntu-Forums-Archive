---
title: "Multimedia Keyboard Buttons"
date: 2007-01-22
forum: Desktop Environments
---

### Post by bsalt on 2007-01-22
Hey guys, I have an HP 2506U Multimedia Keyboard. It has CD/DVD buttons, internet buttons, and a few others. I have gotten all of the buttons to do what I want except for a volume knob on the keyboard. Does anybody know how to assign a knob to do volume functions? Right now I am using two buttons to do the job, but I'm wasting the buttons and the volume knob is useless - and I can't hold down the buttons I assigned; I have to tap the button many times to turn the volume up or down.

I tried moving the volume knob when customizing the keyboard, and it did not detect it, so it may just be a lack of driver support, I don't know.

Any help would be appreciated!

Jon

---

### Post by RedSquirrel on 2007-01-23
I guess you used 'xev' while you were configuring the other buttons, right?

I'm pretty sure if you get no response from xev when you press a button (or move the knob, in your case) then you cannot use that button in linux.

---

### Post by bsalt on 2007-02-23
bump

---

### Post by bsalt on 2007-02-24
I've got the HP multimedia keyboard - serial SK-2506U - and I was wondering if there was a way to force a button to work in Ubuntu - the volume knob.

Anybody know?

---

### Post by dkg on 2007-04-16
I've got an HP P/N 5183-9960  (Model 6511-SU) keyboard with a knob on it as well.  I notice that you didn't answer the question above about xev.

When i run xev and focus the xev window, and i spin the knob on the keyboard, there is no output emitted.

Is there some other way that i can look for signals from the keyboard?  It's a USB keyboard.  It shows up under lshw like this:

```
              *-usb
                   description: USB hub
                   product: Multimedia Keyboard Hub
                   vendor: HP
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=3 speed=12.0MB/s
                 *-usb:0
                      description: Keyboard
                      product: Multimedia Keyboard Hub
                      vendor: HP
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=0mA speed=12.0MB/s
```
And lsusb shows the following:
```
0 butler:~# for foo in 1:2 1:3; do lsusb -v -s $foo; done

Bus 001 Device 002: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0         8
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x010c Multimedia Keyboard Hub
  bcdDevice            0.01
  iManufacturer           1 HP
  iProduct                2 Multimedia Keyboard Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          2 Multimedia Keyboard Hub
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              2 Multimedia Keyboard Hub
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
  wHubCharacteristic 0x000d
    Per-port power switching
    Compound device
    Per-port overcurrent protection
  bPwrOn2PwrGood       22 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 003: ID 03f0:020c Hewlett-Packard Multimedia Keyboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x020c Multimedia Keyboard
  bcdDevice            0.01
  iManufacturer           1 HP
  iProduct                2 Multimedia Keyboard Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          2 Multimedia Keyboard Hub
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
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              2 Multimedia Keyboard Hub
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
         Report Descriptors: 
           ** UNAVAILABLE **
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              2 Multimedia Keyboard Hub
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     167
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval             255
Device Status:     0x0000
  (Bus Powered)

```

Maybe it's the mysterious second InterfaceDescriptor in device 1:3 above?  Is there a way that i can poke around in that interface without writing a kernel module?

---

### Post by Hexagrapher666 on 2007-09-29
> **dkg said:**
> When i run xev and focus the xev window, and i spin the knob on the keyboard, there is no output emitted.  Is there some other way that i can look for signals from the keyboard?

When [COLOR="Navy"]**xev**[/COLOR] failed to produce output for me, the [COLOR="Navy"]**dmesg**[/COLOR] ring buffer showed the hex codes and scancodes for every key that [COLOR="Navy"]**xev**[/COLOR] missed.  [COLOR="Navy"]**dmesg**[/COLOR] is not interactive in realtime like [COLOR="Navy"]**xev**[/COLOR] is, so you would have to turn the volume knob [in a specific direction] and then execute [COLOR="Navy"]**dmesg**[/COLOR] in a terminal.  The last four lines that [COLOR="Navy"]**dmesg**[/COLOR] displays should show the hex code ("0xXXX") and scancode ("eXXX") of the direction in which you turned the volume knob.

(You may also want to look at this comprehensive [HOWTO for configuring multimedia keyboards in Linux]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys") for further information.)

---

