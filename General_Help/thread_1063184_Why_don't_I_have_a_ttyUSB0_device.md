---
title: "Why don't I have a ttyUSB0 device ?"
date: 2009-02-07
forum: General Help
---

### Post by RanLevy on 2009-02-07
Hi all

I am trying to sync a mobile device to my Ubuntu desktop.
Followed instructions but couldn't solve the following message:

synce-serial-config was unable to find a character device named "ttyUSB0"

looking in the dev folder I see there is no ttyUSB0 device (or anything similar).

What can I do to get such a device ?

Ran

---

### Post by jonlemur on 2009-02-07
Before you plug in your device, open a terminal and type ```
tail -f /var/log/messages
```  Then plug in your device, and post the output here.  Hopefully that will give a hint to what's detected and how it's treated.

---

### Post by RanLevy on 2009-02-08
Hi

The reply I got was 

usb 2-1: new full speed USB device using uhci_hcd and address 2

---

### Post by jonlemur on 2009-02-09
I don't know much about the issue, but if you want to see if it is being given a location in /dev/ you could try ```
ls /dev/ > devices.txt
``` before you plug it in (> to send the output to devices.txt), and ```
ls /dev/ >> devices.txt
``` after you plug it in (>> to append the output to devices.txt without overwriting it), then ```
sort devices.txt | uniq -u devices.txt
``` (There is probably a better way to do that, but it works.)  If there is a device there, perhaps you tell synce-serial-config to use that device.

If you post what mobile device you're trying to sync, perhaps someone else can give some recommendations.

---

