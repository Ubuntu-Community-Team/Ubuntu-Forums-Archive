---
title: "USB problems"
date: 2009-04-13
forum: General Help
---

### Post by ant1060 on 2009-04-13
Could someone please help me : I simply do not know what to do next.
I can no longer get any of my USB devices to show on my desktop any more i.e. they will not automount.
EXCEPT my iPhone which continues to show up as normal.
The problems began in January (see my WEIRD USB behaviour post). Next any three of my four devices would show up on the desktop as long as the iPhone was plugged in first.  If not, then NONE of them showed.
Next : after the iPhone was plugged in the second USB would not show but the third and fourth would.
All of this independent of which USB port I plugged the devices into.
Now : only the iPhone shows up and none of the others at all.
This means I can no longer use my Sony Reader or my USB flash drives.
Could someone please tell me how to crank them all up again?

---

### Post by aaronp on 2009-04-14
Are these devices plugged directly into the USB ports on your PC or do you have some kind of USB hub attached?

Can you plug in the devices and enter this into a terminal:

```
lsusb
```

---

### Post by ant1060 on 2009-04-15
Hi,

Thanks very much for your reply.

The devices are all plugged into the USB ports of my computer (ASUS A6000).  There are four ports.  There is no hub.  It does not matter which combination of ports I try.

This morning the situation has reverted to how it was last week : i.e. 
1) I plug in the iPhone and it shows up immediately
2) whatever I plug in as second usb device, N° 2 does not show (today it was the JetFlash Drive)
3) devices N° 3 and 4 both show up as icons.

Here is the output of lsusb :

ant@anthobox:~$ lsusb
Bus 005 Device 006: ID 054c:031e Sony Corp. 
Bus 005 Device 005: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 005 Device 004: ID 05ac:1292 Apple, Inc. 
Bus 005 Device 003: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks for any help you can give me as this problem (and the unreliability of being able to access my Sony Book Reader Main Memory, Sony Book Reader Storage Card and my 2Gb stick) is so aggravating I am thinking of buying a MacBook Pro instead!!

Best wishes,
/Ant
Bruxelles, Belgique

---

