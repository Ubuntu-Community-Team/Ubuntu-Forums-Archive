---
title: "How to block the USB Port in UBUNTU"
date: 2013-06-27
forum: Desktop Environments
---

### Post by slkamath on 2013-06-27
Hi all,

How to block USB Port ( Pen Drive, Memory Card, Hard Disk etc) in UBUNTU Desktop? I need only printer, keyboard and mouse has to work on that particular port.

Regards

Lokesh Kamath

---

### Post by Cheesemill on 2013-06-27
It should be as simple as blacklisting the usb_storage module...
```
echo "blacklist usb_storage" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by Herbon on 2013-07-08
Nice!!!

---

### Post by slkamath on 2013-07-09
Thanks...

I am not yet tested...

Will test and inform you....

Lokesh Kamath


I have tested and unfortunately it's not working.

I have also tested with the code: (some other person posted in the forum)

At the terminal type

 	Code:

 	for device in $(ls /sys/bus/usb/devices/*/product); do echo $device;cat $device;done 
This will get you a list of usb devices. You can then turn the power off and on to them like so.


Turn it off.

 	Code:
 	echo suspend | sudo tee /sys/bus/usb/devices/[COLOR=Red]XXXX[/COLOR]/power/level 
Turn it on

 	Code:
 	echo on | sudo tee /sys/bus/usb/devices/[COLOR=Red]XXXX[/COLOR]/power/level 
Where XXXX is the device to switch off. 

this one also not working.

---

### Post by tgalati4 on 2013-10-19
Install *acpitool* and turn off the power to the ports.  No power, no go.

tgalati4@Mint14-Extensa ~ $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:02:00.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7

Use the -W switch and the number to turn off the power to each device individually.

Also, can you turn off USB in BIOS?

Unfortunately *acpitool* won't work because that only affects wake-from-sleep.

---

### Post by ian-weisser on 2013-10-19
You can use udev rules for it, too.
See [http://askubuntu.com/questions/44913/can-udev-be-used-udev-rules-to-whitelist-certain-usb-devices](http://askubuntu.com/questions/44913/can-udev-be-used-udev-rules-to-whitelist-certain-usb-devices) for a good discussion.

---

