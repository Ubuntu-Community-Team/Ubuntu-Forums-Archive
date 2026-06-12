---
title: "Is there any way to ignore certain axises for a joystick?"
date: 2009-02-24
forum: Gaming &amp; Leisure
---

### Post by motin on 2009-02-24
I have a PSII -> USB converter which makes the 2 connected gamepads/dancemats recognized as a joystick. Now this wouldn't be too bad if not the device would spam around 20-25 seemlingly random events/sec on axis 13 and 14, making it useless*. 

Is there any easy way to disable these axises? 

If a driver needs modification - what would be the likely driver to need to dive into?

Output of "jstest --event /dev/input/js0":
```
Joystick (XPAd Twin Shock) has 14 axes (X, Y, Z, Rx, Ry, Rz, Throttle, Rudder, Hat0X, Hat0Y, Hat1X, Hat1Y, (null), (null))
 and 24 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC, BtnX, BtnY, BtnZ, BtnTL, BtnTR, BtnTL2, BtnTR2, BtnSelect).

```

(It's these (null)-axises that are problematic...)

Then follows a zintillion of these scrolling down fast across the screen:
```
Event: type 2, time 39603264, number 13, value 0, 
Event: type 2, time 39603288, number 12, value 675
Event: type 2, time 39603296, number 13, value -32767, 
Event: type 2, time 39603320, number 12, value -32093,
Event: type 2, time 39603328, number 13, value 0, 

```

*
> <jm_> what's the point of disabling it?
<motin_0> jm_: these axis (12 and 13) send so many events
 so that in a game when I try to map the buttons
<jm_> motin_0: but why does it bother you? simply ignore them if you don't need them
<motin_0> all buttons get mapped to these axises...
 it's like "press a key on the gamepad and then enter"
<motin_0> and it always detects the Axis 12 high/low or axis 13 high/low
 so i cannot use it in the game


I have tried jscalibrator and jscal, experimenting with values hoping that it would be possible to make the calibration settings ignore the problematic axises, but I haven't succeeded. 

Any tips appreciated!

EDIT: 24-feb-2009 14:03
After playing around with jscal, I now have two separate jscal settings:

This one makes the problematic axises ignored, but screws up the usage of all other buttons and axis:
```
jscal -s 14,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,0,0,-2147483648,-2147483648,1,0,0,0,-2147483648,-2147483648,1,0,0,0,-2147483648,-2147483648,1,0,0,0,-2147483648,-2147483648,1,127,17,144,-4227201,-4227201,1,127,1,128,-4227201,-4227201 /dev/input/js0
jstest --event /dev/input/js0
```

This one restores the other buttons and axis, but also has the null-axises enabled:
```
jscal -s 14,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,127,0,127 /dev/input/js0
jstest --event /dev/input/js0 | grep -v "number 12" | grep -v "number 13" # shows that buttons work as expected

```

There _must_ be a way of combinating these... But they are very different in format. Any ideas?

EDIT: 24-feb-2009 14:17

I am back to the original question. Found that this effectively at least makes the problematic axises return no events while gamepad is resting (!):
```
jscal -s 14,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,127,17,144,-4227201,-4227201,1,127,1,128,-4227201,-4227201 /dev/input/js0
```
(that is the successful combination of the two above)

But then, when pressing left or down (which in itself return proper axis 0 and 1 events), the prob-axises starts spamming events... So again I'd really need a way to ignore events from these axises in full!

Any ideas?

For search engines to pick up: The converter model is of ACPP-7388, imported to Sweden by Clas Ohlsson (simply named "USB Adaptor" (yes that spelling) on the blueish packaging.

lsusb output:
```
04d9:0002 Holtek Semiconductor, Inc.
```

lsusb -v output:
```
Bus 004 Device 020: ID 04d9:0002 Holtek Semiconductor, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04d9 Holtek Semiconductor, Inc.
  idProduct          0x0002 
  bcdDevice            1.07
  iManufacturer           1 XPAd
  iProduct                2 Twin Shock
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     170
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
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by motin on 2009-02-24
Solved! 

By using the patched jscal from [this thread]("http://ubuntuforums.org/showthread.php?t=761044"), I was able to switch around the axis in a way that one of them effectively became ignored, and the other one is only triggered mad when I press the start button, which is ok since at least all the important buttons and axis are left. 

Then, with some more calibration and experimenting, I finally came up with values/commands for the patched jcal version that allows me to use the converter for my two gamepads (or dance mats) on linux:

```

./jscal -u 14,0,1,2,3,4,5,6,7,16,27,28,29,40,40,24,288,289,290,291,292,293,294,295,296,297,298,299,300,301,302,303,304,305,306,307,308,309,310,311 /dev/input/js0
./jscal -s 14,1,0,128,128,4194176,4227201,1,0,128,128,4194176,4227201,1,0,128,128,-2147483648,-2147483648,1,0,128,128,4194176,4227201,1,0,128,128,4194176,4227201,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,1,0,128,128,-2147483648,-2147483648,0,0,0,0,0,0,0,0,1,0,0,144,-2147483648,-2147483648,1,143,1,176,-3067740,-3067740 /dev/input/js0

```

The "only" thing left is to solve the [Joystick_Axes_Problem]("http://www.stepmania.com/wiki/Joystick_Axes_Problem")... but that will need to be another thread. 

Cheers!

EDIT: Solved the last problem with soldering. I have supplied soldering instructions for this mat on the official wiki site.

---

