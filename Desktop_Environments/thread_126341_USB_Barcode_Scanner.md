---
title: "USB Barcode Scanner"
date: 2006-02-06
forum: Desktop Environments
---

### Post by GSMD on 2006-02-06
Hello.
I've got a generic USB Barcode scanner that detects and works just fine under WinXP. But not under Ubuntu.
When I scan a barcode, nothing happens. What should I do?

Thank you.

---

### Post by Ampersand on 2006-02-06
Try plugging it in, then typing in a terminal:
```
dmesg | tail
```
to see whether it's been detected.

For a slightly more user-friendly version, try installing (from apt) and running usbview.

Youi might be able to get more information here:
[http://www.qbik.ch/usb/devices/index.php](http://www.qbik.ch/usb/devices/index.php)

---

### Post by GSMD on 2006-02-06
Thank you for such a quick response.
I get
```
 [4296557.082000] usb 1-1: new low speed USB device using uhci_hcd and address 95
[4296557.327000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296557.641000] usb 1-1: USB disconnect, address 95
[4296557.842000] usb 1-1: new low speed USB device using uhci_hcd and address 96
[4296558.042000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296558.408000] usb 1-1: USB disconnect, address 96
[4296557.082000] usb 1-1: new low speed USB device using uhci_hcd and address 95
[4296557.327000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296557.641000] usb 1-1: USB disconnect, address 95
[4296557.842000] usb 1-1: new low speed USB device using uhci_hcd and address 96
[4296558.042000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296558.408000] usb 1-1: USB disconnect, address 96
[4296557.082000] usb 1-1: new low speed USB device using uhci_hcd and address 95
[4296557.327000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296557.641000] usb 1-1: USB disconnect, address 95
[4296557.842000] usb 1-1: new low speed USB device using uhci_hcd and address 96
[4296558.042000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296558.408000] usb 1-1: USB disconnect, address 96
[4296557.082000] usb 1-1: new low speed USB device using uhci_hcd and address 95
[4296557.327000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296557.641000] usb 1-1: USB disconnect, address 95
[4296557.842000] usb 1-1: new low speed USB device using uhci_hcd and address 96
[4296558.042000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296558.408000] usb 1-1: USB disconnect, address 96
[4296557.082000] usb 1-1: new low speed USB device using uhci_hcd and address 95
[4296557.327000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296557.641000] usb 1-1: USB disconnect, address 95
[4296557.842000] usb 1-1: new low speed USB device using uhci_hcd and address 96
[4296558.042000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v34a)] on usb-0000:00:1d.0-1
[4296558.408000] usb 1-1: USB disconnect, address 96
```

The link didn't lead me to any useful unformation :(.
Any ideas?
Thanks.

---

### Post by Ampersand on 2006-02-06
I can't seem to find much about it. if you look try the command
```
lsusb
```
you can see whether it's been detected. I couldn't find any programs for reading barcodes in the Ubuntu repositories, you might be able to find something on [http://www.sourceforge.net](http://www.sourceforge.net) .

---

### Post by GSMD on 2006-02-07
Actually it should simply imput characters like a keyboard does. So I guess there is no need for special software.

---

### Post by Yumi on 2006-03-08
Did you solve the problem, I am coming up to this  and it would be nice to learn from your experience.
Michael

---

### Post by GSMD on 2006-03-09
No, the problem is unresolved.

---

### Post by benji.wakely on 2006-07-11
I also have pretty much the exact same problem - the output differs slightly:

```

Jul 11 15:32:11 mondas kernel: [4295936.363000] usb 2-3: new low speed USB device using ohci_hcd and address 105
Jul 11 15:32:11 mondas kernel: [4295936.489000] input: USB HID v1.00 Keyboard [TechScan Korea Barcode reader(v36a)] on usb-0000:00:03.1-3
Jul 11 15:32:11 mondas kernel: [4295936.504000] usb 2-3: USB disconnect, address 105
Jul 11 15:32:11 mondas input.agent[16355]:      evdev: already loaded

```

Over and over.

Did you find a solution to the problem?

--Benji

---

### Post by benji.wakely on 2006-07-11
The problem seems to be with the ps2 --> usb adaptor - I get the /var/log/messages output with or without the barcode scanner plugged in.

I've worked around this problem by getting a usb keyboard and plugging the barcode scanner into the ps2 port...

--Benji

---

### Post by Yumi on 2006-07-18
Bought myself a cheap Barcode Scanner SD2000 SmartPro CCD. Plugged it into a USB port. Works without installing anything under Drapper Drake.

---

### Post by Slade Winstone on 2006-08-08
Hi,

Has anybody had any luck with the TechScan Korea Barcode reader(v3xx)?

I have a TSK-800 (from the TechScan site at [http://www.techscan.co.kr/product/product_scan1.php](http://www.techscan.co.kr/product/product_scan1.php) ).

I've googled a bit and from reading some similar bug reports it looks like the reader might not be responding to device interrogation requests, leading to all the crashing and disconnects I keep seeing in dmesg.

The point of all this is that the TSK-800 has a "plugable/swapable" tail (i.e. you can buy a new lead/tail and open the unit and swap out the lead/tail from a PS/2 to USB or vice versa).  Mine initially had a PS/2 wedge cable (which I will be swapping back to! :)) and I tried replacing it with a  usb tail...  

So, for any TSK-800 running USB, out there, I would suggest that you try contacting TechScan and getting a PS/2 tail and swapping the USB cable out for a PS/2 one.

Slade.

---

### Post by HomerSimpson748 on 2006-09-13
See if this thread helps. [http://ubuntuforums.org/showthread.php?t=137287]("http://ubuntuforums.org/showthread.php?t=137287")

---

### Post by daller on 2006-10-31
Please everyone, go and contribute your knowledge here:
 
 [https://help.ubuntu.com/community/BarcodeReaders](https://help.ubuntu.com/community/BarcodeReaders)

Does anyone know of a barcode generator for linux?

---

### Post by mexlinux on 2007-02-12
> **daller said:**
> 
Does anyone know of a barcode generator for linux?

[http://www.kbarcode.net/](http://www.kbarcode.net/)

You can also simply get a barcode font from the net.

---

### Post by HomerSimpson748 on 2007-02-13
I used a code 39 TTF (freeware) in an inventory system with great success for some time. We've since upgraded to label printers that have fonts built in.

---

