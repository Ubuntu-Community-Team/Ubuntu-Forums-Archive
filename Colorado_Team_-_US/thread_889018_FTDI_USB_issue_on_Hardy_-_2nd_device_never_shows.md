---
title: "FTDI USB issue on Hardy - 2nd device never shows"
date: 2008-08-13
forum: Colorado Team - US
---

### Post by lcox on 2008-08-13
FYI - I live in Monument, CO and thought I'd ask this question more "locally" instead of globally.

I have an Ubuntu 64 bit Hardy running in a VM on Fusion on my Mac.  I also have 6 identical FTDI based USB devices I want to attach and talk to them.

If I attach the first device, after a bit I see a /dev/ttyUSB0 show up and the appropriate log messages showing a connection appear in the /var/log/messages.  So far, so good.

When I attach the 2nd device, I never see another /dev/tty-anything show up.  If I disconnect the first device, and reconnect the 2nd device, the 2nd device now shows up as /dev/ttyUSB0.

It acts like it can only recognize one of these devices at a time.  

When I connect the 2nd device, there are no log messages in /var/log/messages on a physical connect or disconnect. 

I've also tried another approach which is to connect the devices when the VM is not active, so the devices are recognized by Mac OS X and show up as:

tty.usbserial-A9003PjA
tty.usbserial-A9003Plt 

Back in the Fusion VM, the VM Settings dialog will list two Future Devices USB devices and I can enable them and connect them.  But the same thing happens.  As soon as I enable/connect the first one through the Settings dialog of the VM, I see a /dev/ttyUSB0 show up but when I connect the 2nd one, nothing happens.

Any clues about why Ubuntu is not enumerating more than one of these FTDI devices?   (And I do not see any brltty errors and just in case, I did an apt-get remove brltty, so it's not in the picture anyway.)

---

### Post by joey on 2008-08-13
When you attach the other devices, are you able to see them when you run this? ```
lsusb
```  It's very rare but if they have identical id's that might cause you some grief.  I've never seen this happen before though.  Note: ```
man lsusb
``` ...for more options to get more detail from the devices.

---

### Post by lcox on 2008-08-14
lsusb only shows one device.  Adding the second does not show anything new via lsusb or via the log/messages.

I know the devices are ID'd differently because when I plug them into my Mac they show up as:

tty.usbserial-A9003PjA
tty.usbserial-A9003Plt

If they were ID'd differently, I don't think OS X could differentiate them like this.

I have one native (non-VM) ubuntu box that I will try the same test on and see if it's possibly related to the VM vs the OS.

Any other ideas are welcome.

---

### Post by lcox on 2008-08-14
I hooked this same set of USB devices to a native Ubuntu Fiesty.  At first it had the typical brltty conflict with FTDI, so I corrected it by:

apt-get remove brltty

and rebooted.  After that both devices showed up fine as ttyUSB0 and ttyUSB1 on that machine.

So, since I was running Hardy on the VMs that are having an issue, I don't know for sure yet whether it's a VM-related issue or wether it's Hardy vs Fiesty.

I think I'll get a copy of Fiesty on the same VMWare Fusion and see if it works for that and try to eliminate the distro as a variable.

---

### Post by Keen101 on 2008-09-05
Yes, the [Arduino site]("http://www.arduino.cc/playground/Learning/Linux") 
say's to remove the brltty package. Apparently it causes a problem with the ftdi chips on the Arduino's.

I wonder if your devices are Arduino AVR Microcontrollers?

---

