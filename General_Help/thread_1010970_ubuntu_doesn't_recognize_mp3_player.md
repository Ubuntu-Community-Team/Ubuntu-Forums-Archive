---
title: "ubuntu doesn't recognize mp3 player"
date: 2008-12-14
forum: General Help
---

### Post by oilspot on 2008-12-14
My daughter has a mp3 player. She want's to put new music. Didn't think it would be any problem but when I plug it into the usb ubuntu doesn't recognize it or even acknowledge that it's even there. 

 Don't think it will matter but the mp3 player is a memorex mmp8568-hit

---

### Post by hikaricore on 2008-12-14
Well if it's just a flashdrive type mp3 player it should work, however if it requires special software on Windows and you can't just drop files on it you may have problems.

Check the output of:

> dmesg

Before and after plugging in the device.
Post the last few lines where you'll notice it's changed.

This way we can tell if the device is even being recognized or not.

---

### Post by oilspot on 2008-12-14
with it plugged in

[ 5959.343940]  sdd: sdd1
[19331.333308] usb 5-6: USB disconnect, address 7
[19336.120008] usb 5-6: new high speed USB device using ehci_hcd and address 8
[19336.255874] usb 5-6: configuration #1 chosen from 1 choice
 
 with it unplugged 

[ 5959.343940]  sdd: sdd1
[19331.333308] usb 5-6: USB disconnect, address 7
[19336.120008] usb 5-6: new high speed USB device using ehci_hcd and address 8
[19336.255874] usb 5-6: configuration #1 chosen from 1 choice
[19538.183199] usb 5-6: USB disconnect, address 8

and then i plugged it back in

[ 5959.343940]  sdd: sdd1
[19331.333308] usb 5-6: USB disconnect, address 7
[19336.120008] usb 5-6: new high speed USB device using ehci_hcd and address 8
[19336.255874] usb 5-6: configuration #1 chosen from 1 choice
[19538.183199] usb 5-6: USB disconnect, address 8
[19718.819420] usb 5-5: new high speed USB device using ehci_hcd and address 9
[19718.955875] usb 5-5: configuration #1 chosen from 1 choice





 Is that what you needed?

---

