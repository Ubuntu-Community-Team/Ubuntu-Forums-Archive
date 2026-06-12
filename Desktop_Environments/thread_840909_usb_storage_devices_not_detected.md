---
title: "usb storage devices not detected"
date: 2008-06-25
forum: Desktop Environments
---

### Post by pac-man on 2008-06-25
Hi, I'll describe how my problem happened:

First I was using xubuntu 7.10 and all the external storage devices were working properly (an external hard drive and a card reader). Then I decided to upgrade the distribution to 8.10 (surprisingly, it installed ubuntu, not xubuntu). The external storage devices work properly after the upgrade.

I had the system set up on 2 IDE hard disks, since I needed to remove one, I decided to do a clean installation of ubuntu (this time not xubuntu) 8.04, but to my surprise, now the external HDD nor the external card reader don't work at all!

Did a dmesg and the returned results are:

[   84.522668] usb 4-8: new high speed USB device using ehci_hcd and address 3
[   84.634550] usb 4-8: device descriptor read/64, error -32
[   84.850322] usb 4-8: device descriptor read/64, error -32
[   85.066092] usb 4-8: new high speed USB device using ehci_hcd and address 4
[   85.178011] usb 4-8: device descriptor read/64, error -32
[   85.393745] usb 4-8: device descriptor read/64, error -32
[   85.609513] usb 4-8: new high speed USB device using ehci_hcd and address 5
[   86.017079] usb 4-8: device not accepting address 5, error -32
[   86.128961] usb 4-8: new high speed USB device using ehci_hcd and address 6
[   86.536528] usb 4-8: device not accepting address 6, error -32
[  254.437752] usb 4-8: new high speed USB device using ehci_hcd and address 7
[  254.549584] usb 4-8: device descriptor read/64, error -32
[  254.765241] usb 4-8: device descriptor read/64, error -32
[  254.980905] usb 4-8: new high speed USB device using ehci_hcd and address 8
[  255.092732] usb 4-8: device descriptor read/64, error -32
[  255.308387] usb 4-8: device descriptor read/64, error -32
[  255.524056] usb 4-8: new high speed USB device using ehci_hcd and address 9
[  255.931412] usb 4-8: device not accepting address 9, error -32
[  256.043245] usb 4-8: new high speed USB device using ehci_hcd and address 10
[  256.450600] usb 4-8: device not accepting address 10, error -32


and the lsusb command show nothing but the mouse:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0458:000e KYE Systems Corp. (Mouse Systems) VideoCAM Web
Bus 001 Device 001: ID 0000:0000  

Can anyone help me? I depend a lot on my external drive and I don't really wanna go back to windows. I'm a bit disappointed with this 8.04 release, it looks like ubuntu reached its highest point on the 6.x releases and then it's a downwards spiral getting worse.

Thanks in advance!

---

### Post by pac-man on 2008-06-26
I found a way to access the drive, I typed:

sudo modprobe -r ehci_hcd

But now whenever I plug the drive, it uses the ohci_hcd module, this uses the USB 1.1 speed on a port that used to use the USB 2.0 speed.

ANybody knows how to fix this?

---

### Post by schweigi42 on 2009-01-12
If it works at low speed (ohci) but not at high speed - maybe your cable makes the problem. It could be a contact problem or too long or ...? Just try another cable...

---

