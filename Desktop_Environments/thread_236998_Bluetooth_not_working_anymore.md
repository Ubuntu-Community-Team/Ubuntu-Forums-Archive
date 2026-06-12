---
title: "Bluetooth not working anymore"
date: 2006-08-15
forum: Desktop Environments
---

### Post by koma77 on 2006-08-15
I have an USB Bluetooth dongle that I use with my mobile phone.

Once it worked in Ubuntu, but now I cannot get it to work anymore!

If I do an lsmod I can see: 
bluetooth              49892  5 rfcomm,l2cap,hci_usb

And in dmesg I get:
[17190549.184000] usb 2-3.5: new full speed USB device using ehci_hcd and address 7
[17190549.280000] hci_cmd_task: hci0 command tx timeout

I don't have anything in my /etc/bluetooth/ anymore... (?)

What's going on? Any ideas?

Cheers

---

