---
title: "Genius pen fine tuning"
date: 2011-12-01
forum: Desktop Environments
---

### Post by Arnoldijzermans on 2011-12-01
Hi all

Using a G-pen 450 tablet on 11.10.

For the first time, it is automatically recognized when plugging it in.
In Lucid you had to install the wizardpen driver to activate it, so that looks like a big plus, but....

The problem I had with the pen in Lucid is also present here. 
It is too sensitive, resulting in dragging mails around within Thunderbird and starting applications without actually clicking on it.

Within Lucid I was able to edit the Xorg.conf, or the Wizardpen-fdi.
Xorg.conf does not contain info about the tablet anymore and adding some lines there resulted in not starting up anymore. The 70-wizardpen.fdi is not present anymore.

Anyone of you any idea how to fine tune it now? 

thanks

---

### Post by Favux on 2011-12-01
Hi Arnoldijzermans,

From the sound of things the tablet is on the evdev driver now, so that's how you'd want to configure it, with an evdev.conf.  To check find the "device name" for the tablet with:
```
xinput list
```
then run, with the quotes:
```
xinput list-props "device name"
```
and post the outputs.

You'd put a custom .conf in /etc/X11/xorg.conf.d.  The distribution puts their .conf's in /usr/share/X11/xorg.conf.d.  So call it something like Gpen450-on-evdev.conf?

---

### Post by Arnoldijzermans on 2011-12-05
hi mate

Sorry for the somewhat late reply. Ran into a little problem

Xinput

[COLOR=DarkSlateBlue]&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=8    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                     id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
[/COLOR]
As you can see I have to UC Logic tablets listed. (only one attached though).
The second command including the device name thus returns.
[COLOR=DarkSlateBlue]Warning: There are multiple devices matching 'UC-LOGIC Tablet WP5540U'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device UC-LOGIC Tablet WP5540U[/COLOR]

Fyi. I did a fresh install, so nothing left behind.
Is there a way to list it using the ID?

Thanks in advance

---

### Post by marinara on 2011-12-05
yeah just 
xinput list-props 9
or 
xinput list-props 10

---

### Post by Arnoldijzermans on 2011-12-07
Thanks

Here is ID 9

[COLOR=DarkRed]Device 'UC-LOGIC Tablet WP5540U':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (240):    0
    Device Accel Constant Deceleration (241):    1.000000
    Device Accel Adaptive Deceleration (242):    1.000000
    Device Accel Velocity Scaling (243):    10.000000
    Evdev Axis Inversion (244):    0, 0
    Evdev Axis Calibration (245):    <no items>
    Evdev Axes Swap (246):    0
    Axis Labels (247):    "Abs X" (257), "Abs Y" (258), "Abs Pressure" (259)
    Button Labels (248):    "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (249):    0
    Evdev Middle Button Timeout (250):    50
    Evdev Wheel Emulation (251):    0
    Evdev Wheel Emulation Axes (252):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (253):    10
    Evdev Wheel Emulation Timeout (254):    200
    Evdev Wheel Emulation Button (255):    4
    Evdev Drag Lock Buttons (256):    0[/COLOR]

And ID 10

[COLOR=DarkRed]Device 'UC-LOGIC Tablet WP5540U':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (240):    0
    Device Accel Constant Deceleration (241):    1.000000
    Device Accel Adaptive Deceleration (242):    1.000000
    Device Accel Velocity Scaling (243):    10.000000
    Evdev Axis Inversion (244):    0, 0
    Evdev Axis Calibration (245):    <no items>
    Evdev Axes Swap (246):    0
    Axis Labels (247):    "Abs X" (257), "Abs Y" (258), "Abs Pressure" (259)
    Button Labels (248):    "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (249):    0
    Evdev Middle Button Timeout (250):    50
    Evdev Wheel Emulation (251):    0
    Evdev Wheel Emulation Axes (252):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (253):    10
    Evdev Wheel Emulation Timeout (254):    200
    Evdev Wheel Emulation Button (255):    4
    Evdev Drag Lock Buttons (256):    0[/COLOR]

---

### Post by Arnoldijzermans on 2011-12-07
They look similar to me.

Is it normal to have a double entry?
Well very curious where and how to adjust stuff.

Learning again :-) 

thanks

---

### Post by Favux on 2011-12-07
No, not normal to have a double entry unless the tablet has two devices that are exported separately from the kernel, say a stylus and a tablet mouse.

So there are basically several possible cases.
1) It's doing what it is suppose to or it is a bug in the kernel driver.
2) Or the bug is the kernel driver isn't naming them as different devices.
3) Or the kernel part is working right and it expects the X driver to figure out the different devices and append the device type to their name.  But the WizardPen driver never handled the tablet mouse as far as I know.  I think evdev can handle both a stylus and a mouse so the "bug" would be evdev isn't distinguishing between them.

One possibility is if we do an attribute walk on both devices we might find a difference in the name somewhere or a different binary interface number or something.  If so then we might be able to write a udev rule to distinguish between them so then evdev knows it has two different things.  So you want to run the following for both event #'s and post the outputs:
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event?)
```
You can get the event number for each device in the Xorg.0.log (/var/log) where each device is being set up.

In the meantime your basic 52-wizardpen-on-evdev.conf file would look like this:
```
Section "InputClass"
        Identifier "wizardpen-on-evdev class"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```
To create or edit it:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf
```
Then using man evdev (in a terminal) and whatever else we can find we could start testing Options.  Say:
```
Section "InputClass"
        Identifier "wizardpen-on-evdev class"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "TopZ" "1"
        Option "BottomZ" "1023"
EndSection
```
The list-props outputs appear to show evdev isn't aware of your tablet's coordinates so we could try setting them starting with pressure/z-axis.  That's assuming you have 1024 pressure levels and it is setting a Threshold of 1.  Since your stylus is oversensitive you might want to increase the threshold to 10 then 20 etc. and see if a higher setting is good.  That's assuming we have the correct syntax.

---

### Post by Arnoldijzermans on 2011-12-08
thanks will give it a try tomorrow.

Will post the outcome here.

cheers

---

### Post by Arnoldijzermans on 2011-12-09
the output of the **udevadm** command

[COLOR=Black]**event5**[/COLOR]
[COLOR=DarkRed]  looking at device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1/3-1:1.0/input/input5/event5':
    KERNEL=="event5"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1/3-1:1.0/input/input5':
    KERNELS=="input5"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="UC-LOGIC Tablet WP5540U"
    ATTRS{phys}=="usb-0000:05:00.0-1/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1/3-1:1.0':
    KERNELS=="3-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{interface}=="Tablet WP5540U"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="35"
    ATTRS{idVendor}=="5543"
    ATTRS{idProduct}=="0004"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="UC-LOGIC"
    ATTRS{product}=="Tablet WP5540U"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="21"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-13-generic-pae xhci_hcd"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{serial}=="0000:05:00.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0':
    KERNELS=="0000:05:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{vendor}=="0x1b6f"
    ATTRS{device}=="0x7023"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{subsystem_device}=="0x5007"
    ATTRS{class}=="0x0c0330"
    ATTRS{irq}=="41"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.2':
    KERNELS=="0000:00:1c.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x1c14"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{subsystem_device}=="0x5001"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""[/COLOR]

Event6
[COLOR=DarkRed]
  looking at device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1/3-1:1.0/input/input6/event6':
    KERNEL=="event6"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1/3-1:1.0/input/input6':
    KERNELS=="input6"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="UC-LOGIC Tablet WP5540U"
    ATTRS{phys}=="usb-0000:05:00.0-1/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1/3-1:1.0':
    KERNELS=="3-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{interface}=="Tablet WP5540U"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="35"
    ATTRS{idVendor}=="5543"
    ATTRS{idProduct}=="0004"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="1.5"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="UC-LOGIC"
    ATTRS{product}=="Tablet WP5540U"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="21"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0300"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.0.0-13-generic-pae xhci_hcd"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{serial}=="0000:05:00.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1c.2/0000:05:00.0':
    KERNELS=="0000:05:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{vendor}=="0x1b6f"
    ATTRS{device}=="0x7023"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{subsystem_device}=="0x5007"
    ATTRS{class}=="0x0c0330"
    ATTRS{irq}=="41"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.2':
    KERNELS=="0000:00:1c.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x1c14"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{subsystem_device}=="0x5001"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""[/COLOR]

---

### Post by Arnoldijzermans on 2011-12-09
Favux

works like a charm, well will be. Just trying to get the right config now, but it's getting better and better. Thanks.

---

### Post by Favux on 2011-12-09
Outstanding!  :)

Feel free to post what you have or what you end up with.

Looking at the attributes walks both events appear to be the same device, not say a stylus and a mouse.  No differences I can see.  Luckily it looks like the driver is able to deal with that because I think that means there is a kernel bug.

---

### Post by Arnoldijzermans on 2011-12-09
Well this is the 52-wizardpen-on-evdev.conf file as I use ut now wit my Genius G-Pen 450.
Thanks for the help:popcorn:

[COLOR=DarkRed]Section "InputClass"
        Identifier "wizardpen-on-evdev class"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option          "TopX"          "2199"
        Option          "TopY"          "3598"
        Option          "BottomX"       "30325"
        Option          "BottomY"       "29278"
        Option "TopZ" "50"
        Option "BottomZ" "1023"
EndSection[/COLOR]

---

### Post by Favux on 2011-12-09
Thanks for posting that.

Since 0 is a level, if your hardware is rated at 1024 pressure levels, then the range is 0 to 1023.  So change to:
```
Option "BottomZ" "1023"
```
and you're good.

---

### Post by Arnoldijzermans on 2011-12-10
done :P

---

### Post by GangrN on 2012-01-08
Hello ubuntu forums

I am under Oneiric and using a genius mousepen UC-LOGIC WP8060U, which uses a mouse and a pen. Both seem to be supported, but pen is not calibrated well for drawing (erratic stains and lines sprouting randomly towards the upper-left corner when I draw under gimp).

I have read the thread and seen that I have no 52-wizardpen-on-evdev.conf file.
Event8 is my pen, event9 is my tablet mouse.

xinput list-props 8
```
Device 'UC-LOGIC Tablet WP8060U':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    0
    Device Accel Constant Deceleration (266):    1.000000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    10.000000
    Evdev Axis Inversion (269):    0, 0
    Evdev Axis Calibration (270):    <no items>
    Evdev Axes Swap (271):    0
    Axis Labels (272):    "Abs X" (262), "Abs Y" (263), "Abs Pressure" (264)
    Button Labels (273):    "Button Unknown" (261), "Button Unknown" (261), "Button Unknown" (261), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
    Evdev Middle Button Emulation (274):    0
    Evdev Middle Button Timeout (275):    50
    Evdev Wheel Emulation (276):    0
    Evdev Wheel Emulation Axes (277):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (278):    10
    Evdev Wheel Emulation Timeout (279):    200
    Evdev Wheel Emulation Button (280):    4
    Evdev Drag Lock Buttons (281):    0
```xinput list-props 9
```
Device 'UC-LOGIC Tablet WP8060U':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    0
    Device Accel Constant Deceleration (266):    1.000000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    10.000000
    Evdev Axis Inversion (269):    0, 0
    Evdev Axes Swap (271):    0
    Axis Labels (272):    "Rel X" (152), "Rel Y" (153)
    Button Labels (273):    "Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
    Evdev Middle Button Emulation (274):    0
    Evdev Middle Button Timeout (275):    50
    Evdev Wheel Emulation (276):    0
    Evdev Wheel Emulation Axes (277):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (278):    10
    Evdev Wheel Emulation Timeout (279):    200
    Evdev Wheel Emulation Button (280):    4
    Evdev Drag Lock Buttons (281):    0

```I neither have /etc/X11/xorg.conf.d folder, only /usr/share/X11/xorg.conf.d

Am I correct if I assume I can create the "52" file in it

And am I correct assuming I have to write it this way:
```

Section "InputClass"
         Identifier "wizardpen-on-evdev class"
         MatchIsTablet "on"
         MatchDevicePath "/dev/input/event8"
         Driver "evdev"
         Option "TopZ" "1"
         Option "BottomZ" "1023" 
EndSection
```And can someone tell me if it will cause me some issues with my tablet mouse
or if I am wrong doing this and if there is an other option to calibrate my pen.

Thank you.

---

### Post by Favux on 2012-01-08
Hi GangrN,

Welcome to Ubuntu forums!

There is a bug in Oneiric which is obvious in Gimp because of Gimp's history buffer.  So use this PPA which has a patch applied to the default Gimp to turn off the history buffer:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)  That makes it usable.  See this Launchpad bug:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)

You do not need a 52-evdev.conf.  The evdev driver should just work for your tablet if it's hid driver in the kernel is set up correctly.  This means there is no way to set up unknown (not listed in the kernel) tablets though.

I was talking with an evdev developer the other day and it turns out there is no way to change Z-axis settings on evdev like there was with the WizardPen driver.  Code just not there in the driver.  I pointed out that while that may be OK for models that have the correct pressure levels listed in the kernel it does not allow the tablet user to set a Pressure Threshold.  And setting a Threshold (something like "TopZ") is needed for some tablets.  So they're aware of that now.  Hopefully that will be added to evdev at some point.

---

### Post by GangrN on 2012-01-08
Wow, thank you for the flash answer, you are amazing. I am glad I asked!

Works like a charm, thank you

---

### Post by GangrN on 2012-01-09
Err, I just wondered... this means I won't be able to upgrade to Gimp 2.7?

---

### Post by Favux on 2012-01-09
Supposedly Gimp 2.7 has the history buffer turned off/removed by default because it has been a source of problems.  Presumably 2.7 has other methods to improve stroke quality rather than the history buffer.  But success with installing 2.7 seems variable from what I see.  Maybe worth a shot.  I think the final release before 2.8 may be out.

---

### Post by GangrN on 2012-01-12
> **Favux said:**
> Supposedly Gimp 2.7 has the history buffer turned off/removed by default because it has been a source of problems.  Presumably 2.7 has other methods to improve stroke quality rather than the history buffer.  But success with installing 2.7 seems variable from what I see.  Maybe worth a shot.  I think the final release before 2.8 may be out.

 A side effect of the gimp patch: I experienced several graphic card driver issues
I had issues wth online 3d games and sweethome3d. I first tried to turn on/off ati proprietary drivers but when driver was on java did not work properly, when off online 3d games crashed. Then I wondered why mahjongg and aisleriot were not working any more. I reinstalled the packages via synaptic. Every time synaptic registered the gimp patch as a dependency of the game (aisleriot, gnome-hearts, mahjongg... !!!) to be left unchanged by the re install.

Now everything is working fine...  

:guitar:
Very strange. I hope someone of greater knowledge can see the whole pattern.

---

### Post by nicknow news on 2012-01-13
Hello to everyone!
I have a similar problem with Genius EasyPen M610X tablet as anton_melnikov previously described in this forum about his EasyPen i405x pen behaviour. Pen is movable but can't click, nor do pressure. Here is the system information:

OS: Ubuntu 11.10 ( Desktop )

**$ lsusb**
```
Bus 002 Device 004: ID 0458:5013 KYE Systems Corp. (Mouse Systems)
```

**$ xinput list**
```
Genius EasyPen M610X                    	id=8	[slave  pointer  (2)]
```

**$ xinput list-props "Genius EasyPen M610X"**
```
Device 'Genius EasyPen M610X':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (255):	0
	Device Accel Constant Deceleration (256):	1.000000
	Device Accel Adaptive Deceleration (257):	1.000000
	Device Accel Velocity Scaling (258):	10.000000
	Evdev Axis Inversion (259):	0, 0
	Evdev Axis Calibration (260):	<no items>
	Evdev Axes Swap (261):	0
	Axis Labels (262):	"Abs X" (248), "Abs Y" (249), "Abs Z" (250), "Abs Rotary X" (251), "Abs Rotary Y" (252), "Abs Rotary Z" (253), "Abs Pressure" (254), "None" (0)
	Button Labels (263):	"Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130), "Button Side" (245), "Button Extra" (246), "Button Forward" (247), "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241)
	Evdev Middle Button Emulation (264):	0
	Evdev Middle Button Timeout (265):	50
	Evdev Wheel Emulation (266):	0
	Evdev Wheel Emulation Axes (267):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (268):	10
	Evdev Wheel Emulation Timeout (269):	200
	Evdev Wheel Emulation Button (270):	4
	Evdev Drag Lock Buttons (271):	0
```

I have followed out  instructions that described here and then I created a file **/usr/share/X11/xorg.conf.d/52-wizardpen-on-evdev.conf**

```
Section "InputClass"
        Identifier "wizardpen-on-evdev class"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "TopZ" "1"
        Option "BottomZ" "1023"
EndSection
```

After replug into usb or even restart, nothing is changed, but if  I remap input buttons by command:
**$ xinput set-button-map "Genius EasyPen M610X" 0 0 0 0 0 0 0 1 3 2**
Buttons on pen  is starts working, but without pressure. I do not know in which program I could test pen pressure for sure. Gimp ( 2.6.11 ) is not helping to me with it, because input device settings is not clear enough for understanding what could be wrong with program configuration.
So I am stuck with this issue and don't know where should I start to move away from that point of dead end situation. I hope that someone can help to me out with configuring pressure on the pen. Thanks for your attention.

---

### Post by Favux on 2012-01-14
Hi nicknow news,

Welcome to Ubuntu forums!

There are several KYE Systems Corp. tablet models currently reporting no pressure on the evdev driver.  These models have no Vendor or Product ID match in the compatibility table on Nikolai Kondrashov's DIGImend project site:  [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)

lsusb:
Bus 001 Device 004: ID 0458:5010 KYE Systems Corp. (Mouse Systems)
xinput list:
&#9116;   &#8627; Genius EasyPen i405X                      id=11   [slave  pointer  (2)]

lsusb:
Bus 002 Device 003: ID 0458:5011 KYE Systems Corp. (Mouse Systems)
xinput list:
&#9116;   &#8627; Genius MousePen i608X                     id=9    [slave  pointer  (2)]

lsusb:
Bus 002 Device 004: ID 0458:5013 KYE Systems Corp. (Mouse Systems)
xinput list:
Genius EasyPen M610X                    	id=8	[slave  pointer  (2)]

Vendor ID = 0458 = KYE Systems Corp.
Product ID = 5010 or 5011 or 5013

This indicates the models are not yet supported in the kernel and the usbhid-dump data Nick requests for that tablet needs to be sent in to him so he can add the tablet model to the kernel.  Also see these threads:  [http://ubuntuforums.org/showthread.php?t=1886167&page=2](http://ubuntuforums.org/showthread.php?t=1886167&page=2)  and  [http://ubuntuforums.org/showthread.php?t=1899225&page=2](http://ubuntuforums.org/showthread.php?t=1899225&page=2)

---

### Post by nicknow news on 2012-01-14
Favux, I am glad that you reply and thanks. I have visited DIGImend project site and download tarball archive with usbhid-dump source files then ./configure; make. I started up program from './usbhid-dump-1.2/src' folder  in my case '$ sudo usbhid-dump 2 4'  as I guess it should be the tablet numbers. The program output in first line was:

```
000:DESCRIPTOR                 1326543195.092727
```

Other lines was like hex code "05 0D 09 01 A1  ..... end etc.". Did I do all right or something is wrong? Can you guide me if there was mistake in usbhid-dump command running? I am grateful for your help.

---

### Post by Favux on 2012-01-14
Hi nicknow news,

No, that sounds correct.  If you look at viktoria.s' udump in her usbstuff attachment on this post:  [http://ubuntuforums.org/showpost.php?p=11580830&postcount=22](http://ubuntuforums.org/showpost.php?p=11580830&postcount=22)  You'll see:
```
~$ sudo usbhid-dump --entity=both 2 4
000:DESCRIPTOR                 1325253206.246410
 05 0D 09 01 A1 01 85 07 09 EE A1 00 09 EE 15 00
 25 FF 75 08 95 07 81 06 C0 C0 05 0C 09 01 A1 01
 85 03 15 00 26 FF 02 19 00 2A FF 02 75 10 95 01
 81 00 C0 05 01 09 00 A1 01 85 05 06 00 FF 09 01
 15 81 25 7F 75 08 95 07 B1 02 C0 05 01 09 02 A1
 01 85 08 09 01 A1 00 05 09 19 01 29 03 15 00 25
 01 95 03 75 01 81 02 95 05 81 01 05 01 09 30 09

etc.
```
That, and some other stuff is what Nick needs.  So I am glad to see you are collecting the information for him!  :)

Of course for you the lsusb command would be:
```
sudo lsusb -v -d 0458:5013 
```

---

### Post by nicknow news on 2012-01-14
I hope that participation in providing little information will not harm anybody, of course :)
Nice ! I followed your writings and collected output information. This is what two commands gave to me:

**~$ sudo usbhid-dump --entity=both 2 4**

```
000:DESCRIPTOR                 1326554970.458882
 05 0D 09 01 A1 01 85 07 09 EE A1 00 09 EE 15 00
 25 7F 75 08 95 07 81 06 C0 C0 05 0C 09 01 A1 01
 85 03 15 00 26 FF 02 19 00 2A FF 02 75 10 95 01
 81 00 C0 05 01 09 00 A1 01 85 05 06 00 FF 09 01
 15 81 25 7F 75 08 95 07 B1 02 C0 05 01 09 02 A1
 01 85 08 09 01 A1 00 05 09 19 01 29 03 15 00 25
 01 95 03 75 01 81 02 95 05 81 01 05 01 09 30 09
 31 09 38 09 00 15 81 25 7F 75 08 95 04 81 06 C0
 C0 05 01 09 02 A1 01 85 09 09 01 A1 00 05 09 19
 01 29 03 15 00 25 01 95 03 75 01 81 02 95 04 81
 01 05 0D 09 32 95 01 81 02 05 01 09 30 15 00 26
 00 50 35 00 46 00 50 75 10 95 01 81 02 09 31 15
 00 26 00 32 35 00 46 00 32 75 10 95 01 81 02 C0
 C0 05 0D 09 01 A1 01 85 11 09 EE A1 00 09 EE 15
 00 25 7F 75 08 95 07 81 06 C0 C0 05 0D 09 02 A1
 01 85 10 09 20 A1 00 09 42 09 44 09 3C 09 45 15
 00 25 01 75 01 95 04 81 02 95 03 81 03 09 32 15
 00 25 01 95 01 81 02 05 01 09 30 75 10 95 01 A4
 55 0D 65 33 15 00 26 FF 7F 35 00 46 FF 7F 81 02
 09 31 26 00 64 46 00 64 81 02 05 0D 09 30 15 00
 26 FF 03 35 00 46 FF 03 81 02 75 10 C0 C0 05 0D
 09 01 A1 01 85 14 09 EE A1 00 09 EE 15 00 25 7F
 75 08 95 07 81 06 C0 C0 05 0D 09 01 A1 01 85 13
 09 20 A1 00 09 42 09 44 09 3C 09 45 15 00 25 01
 75 01 95 04 81 02 95 03 81 03 09 32 95 01 81 02
 05 01 09 30 75 10 95 01 A4 55 0D 65 33 15 00 26
 FF 7F 35 00 46 FF 7F 81 02 09 31 26 00 64 46 00
 64 81 02 05 0D 09 30 15 00 26 FF 03 81 02 75 10
 C0 C0 05 0D 09 01 A1 01 85 12 09 EE A1 00 09 EE
 15 00 25 7F 75 08 95 07 81 06 C0 C0
```

.... and some stream if needs.
```
000:STREAM                     1326554973.617861
 09 80 3C 03 00 00 00 00

000:STREAM                     1326554973.619847
 09 80 3C 03 00 00 00 00

000:STREAM                     1326554973.623847
 09 80 3C 03 00 00 00 00

000:STREAM                     1326554973.625846
 09 80 3C 03 00 00 00 00
```

**~$ sudo lsusb -v -d 0458:5013**

```
Bus 002 Device 004: ID 0458:5013 KYE Systems Corp. (Mouse Systems) 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x5013 
  bcdDevice            0.01
  iManufacturer           1 Genius
  iProduct                2 EasyPen M610X
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     476
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
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               2
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled
```

Even if it not fix the issue very soon, it will not disappoint me because that information might be useful for someone and one day it probably change Ubuntu to a bit better. Tell me please if needs any other information for help  the others.

---

### Post by Favux on 2012-01-14
Great!

Say I can't tell from your post, but did you send the information to Nick?  His e-mail link is at the bottom of the DIGImend Project site.

Nikolai Kondrashov <spbnick@gmail.com>

By the way the link is to the DIGImend sourceforge homepage.  For maybe a better overview see:  [http://sourceforge.net/projects/digimend/](http://sourceforge.net/projects/digimend/)

---

### Post by nicknow news on 2012-01-14
Yes, I have already sent a mail to Nick  with collected information that I posted in this thread. Maybe I could sent this earlier before you ask. Thanks again and good luck!

---

