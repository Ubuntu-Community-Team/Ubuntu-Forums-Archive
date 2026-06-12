---
title: "repeated loss of mouse buttons"
date: 2009-02-01
forum: General Help
---

### Post by dutler on 2009-02-01
hello. I am running kubuntu 8.10 with KDE 4.2. I have a USB mouse and have been using my hardware configuration with Kubuntu for well over a year.

Im thinking the KDE upgrade or recent update is the blame....

Periodically, I lose the button functionality of my mouse. I can still move the pointer, but get no response from button clicks. The keyboard works fine.

The only way i know to restore functionality is to restart x - quite a pita when you have your groove on ....

I searched around in the wiki and forum, but only found post that were quite old - thought i should start a new thread.

1) what other info can i provide to help troubleshoot.
2) what could be causing the symptoms?
3) until it gets fixed, what else can i do besides restarting x?

---

### Post by gimcrack on 2009-02-01
Then it's either a kernel/driver bug from an update you've installed, or your mouse button is damaged.

Checkout this thread

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/294738](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/294738)

---

### Post by dutler on 2009-02-01
Thanks gimcrack. i may be having the same troubles, but it is a bit different. For example xev does not provide any output on mouse clicks.

lsusb -v give the following:
> Bus 006 Device 008: ID 046d:c041 Logitech, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc041
  bcdDevice           46.00
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          3
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
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
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      94
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
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
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
        wMaxPacketSize     0x0014  1x 20 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


Xorg.0.log seems to give me both the Macintosh and my Logitech mouse:
> (II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Gaming Mouse
(**) Logitech USB Gaming Mouse: always reports core events
(**) Logitech USB Gaming Mouse: Device: "/dev/input/event4"
(II) Logitech USB Gaming Mouse: Found x and y relative axes
(II) Logitech USB Gaming Mouse: Found 16 mouse buttons
(II) Logitech USB Gaming Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE)
(**) Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

I ll be restarting x and following the direction for a bug report at [https://wiki.ubuntu.com/DebuggingMouseDetection](https://wiki.ubuntu.com/DebuggingMouseDetection)

thanks for the direction.

---

### Post by dutler on 2009-02-01
Check out this bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167)

My case appears to be an issue with Xinerama. 

-tom

---

