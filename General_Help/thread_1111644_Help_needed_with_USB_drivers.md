---
title: "Help needed with USB drivers"
date: 2009-03-30
forum: General Help
---

### Post by Ziphilt on 2009-03-30
I want to connect to a BASIC Stamp 2 and a Propeller chip, which both connect via USB. By checking the man pages on MAKEDEV, I have found that I am missing some files; /dev/ttyUSB{0-15}. I think that those are what I need. (please tell me if that is incorrect) Though when I tried to create them with

cd /dev; sudo MAKEDEV usb

its response was that it was a read-only filesystem. As far as I know, that doesn't make sense because I used sudo.

If you need any more information to help, I will try to get as much as I can find. Thank you for your time.

---

### Post by ibuclaw on 2009-03-30
Attach the devices to your computer, wait a few seconds, then run:
```
dmesg | tail
```
In a terminal.
You should be able to see the detection, and assignment of them.
If not, please post the output.

Regards
Iain

---

### Post by Ziphilt on 2009-03-30
The output when connecting the BOE-Bot:
```
[13479.772734] usbcore: registered new interface driver ftdi_sio
[13479.772740] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[17917.176103] usb 1-1: USB disconnect, address 2
[17917.176834] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[17917.176853] ftdi_sio 1-1:1.0: device disconnected
[28375.140068] usb 1-1: new full speed USB device using uhci_hcd and address 3
[28375.341050] usb 1-1: configuration #1 chosen from 1 choice
[28375.346181] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[28375.346758] ftdi_sio: Detected FT232RL
[28375.347297] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0

```
I don't know what to do with it.

The program I was trying to use for the BOE-Bot told me that /dev/ttyS0 or ttyS1 are defaults. The program that I intend to use for the Propeller Chip refers to /dev/ttyUSB0 and ttyUSB2.

---

### Post by ibuclaw on 2009-03-30
> 
[28375.140068] usb 1-1: new full speed USB device using uhci_hcd and address 3
[28375.341050] usb 1-1: configuration #1 chosen from 1 choice
[28375.346181] ftdi_sio 1-1:1.0: FTDI USB Serial Device converter detected
[28375.346758] ftdi_sio: Detected FT232RL
[28375.347297] usb 1-1: FTDI USB Serial Device converter now attached to ttyUSB0

[QUOTE=Ziphilt]
The program I was trying to use for the BOE-Bot told me that /dev/ttyS0 or ttyS1 are defaults. The program that I intend to use for the Propeller Chip refers to /dev/ttyUSB0 and ttyUSB2.[/QUOTE]

As far as I can tell, the USB device is detected and loaded alright, and it is attached to the **/dev/ttyUSB0** device driver association file, so you should be able to use your program without problems.

A quick scan of the repositories finds this package:
```
**ftdi-eeprom** - Tool for reading/erasing/flashing FTDI USB chip eeproms
```

Regards
Iain

---

### Post by Ziphilt on 2009-03-30
Well, I think my whole problem was that I could not find /dev/ttyUSB0 or any others. When I created a link to /dev/ttyUSB0 called /dev/bstamp (that's how the program works), it was a functioning link, and the program worked correctly just now. I will test the Propeller Chip tomorrow. Thanks for your help!

---

### Post by ibuclaw on 2009-03-30
You required a symlink to get it to work?

hmmm...

If that is the case, to make the symlink automatic every time, find the device path in /sys
```
find /sys -name ttyUSB*
```
and look up the attributes of the directory that should (hopefully) be listed.

ie (A guestimated example of what you should put in next):
```
udevinfo -a -p /sys/class/tty/ttyUSB0
```
and pick a unique attribute to copy.

Next, edit the corresponding udev rules file
```
sudo gedit /etc/udev/rules.d/60-symlinks.rules
```
And put a line in like so:
```

# Create /dev/bstamp symlink for FTDI Device
KERNEL=="ttyUSB*", **ATTRS{product}=="FT232RL"**, \
                    SYMLINK+="bstamp"

```
ATTRS{attr} will be the information taken from the undevinfo command.
Once done, save/quit, then restart udev

```
sudo /etc/init.d/udev restart
```
And when you plug in the USB device again, the symlink /dev/bstamp should be create automagically for you.

Regards
Iain

---

### Post by larytet on 2013-03-03
Just in case anyone needs original EEPROM images which contain USB descriptors and can be programmed


Device:FT4232H (0403/6011)
Product description USB <-> Serial Converter
Serial number FTWASNK1
```
0000: 8888 0304 1160 0008 8032 08F0 0000 9A0A 
0008: A432 D612 0000 0000 6600 0000 0000 0000 
0010: 0000 0000 0000 0000 0000 0000 0000 0000 
0018: 0000 0000 0000 0000 0000 0000 0000 0000 
0020: 0000 0000 0000 0000 0000 0000 0000 0000 
0028: 0000 0000 0000 0000 0000 0000 0000 0000 
0030: 0000 0000 0000 0000 0000 0000 0000 0000 
0038: 0000 0000 0000 0000 0000 0000 0000 0000 
0040: 0000 0000 0000 0000 0000 0000 0000 0000 
0048: 0000 0000 0000 0000 0000 0A03 4600 5400 
0050: 4400 4900 3203 5500 5300 4200 2000 3C00 
0058: 2D00 3E00 2000 5300 6500 7200 6900 6100 
0060: 6C00 2000 4300 6F00 6E00 7600 6500 7200 
0068: 7400 6500 7200 1203 4600 5400 5700 4100 
0070: 5300 4E00 4B00 3100 0000 0000 0000 0000 
0078: 0000 0000 0000 0000 0000 0000 0000 0EE5 

```

Device:FT4232H (0403/6011)
Product description USB <-> Serial Converter
Serial number FTWASNK2
```
0000: 8888 0304 1160 0008 8032 08F0 0000 9A0A 
0008: A432 D612 0000 0000 6600 0000 0000 0000 
0010: 0000 0000 0000 0000 0000 0000 0000 0000 
0018: 0000 0000 0000 0000 0000 0000 0000 0000 
0020: 0000 0000 0000 0000 0000 0000 0000 0000 
0028: 0000 0000 0000 0000 0000 0000 0000 0000 
0030: 0000 0000 0000 0000 0000 0000 0000 0000 
0038: 0000 0000 0000 0000 0000 0000 0000 0000 
0040: 0000 0000 0000 0000 0000 0000 0000 0000 
0048: 0000 0000 0000 0000 0000 0A03 4600 5400 
0050: 4400 4900 3203 5500 5300 4200 2000 3C00 
0058: 2D00 3E00 2000 5300 6500 7200 6900 6100 
0060: 6C00 2000 4300 6F00 6E00 7600 6500 7200 
0068: 7400 6500 7200 1203 4600 5400 5700 4100 
0070: 5300 4E00 4B00 3200 0000 0000 0000 0000 
0078: 0000 0000 0000 0000 0000 0000 0000 0ED5 

```



Device:FT X (0403/6015)
Product description FT230X Basic UART
Serial number DAWEG746
Read EEPROM Device 0
```
0000: 8000 0304 1560 0010 802D 0800 0000 A00A 
0008: AA24 CE12 0000 0000 0000 0901 0205 0000 
0010: 0000 0000 0000 0000 0000 0000 0000 0000 
0018: 0000 0000 0000 0000 0000 0000 0000 0000 
0020: 0000 0000 0000 0000 0000 0000 0000 0000 
0028: 0000 0000 0000 0000 0000 0000 0000 0000 
0030: 0000 0000 0000 0000 0000 0000 0000 0000 
0038: 0000 0000 0000 0000 0000 0000 0000 0000 
0040: 1D36 E2C9 0100 E600 01A0 3000 0000 0000 
0048: 0000 0000 4441 5648 5844 4E39 0000 0000 
0050: 0A03 4600 5400 4400 4900 2403 4600 5400 
0058: 3200 3300 3000 5800 2000 4200 6100 7300 
0060: 6900 6300 2000 5500 4100 5200 5400 1203 
0068: 4400 4100 5700 4500 4700 3700 3400 3600 
0070: 0000 0000 0000 0000 0000 0000 0000 0000 
0078: 0000 0000 0000 0000 0000 0000 0000 790E 

```

---

### Post by howefield on 2013-03-03
Old thread closed.

---

