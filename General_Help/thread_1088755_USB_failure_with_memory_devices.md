---
title: "USB failure with memory devices"
date: 2009-03-06
forum: General Help
---

### Post by criptonite on 2009-03-06
My USB ports have stopped recognising external memory drives.  I've tried three so far, my Freecom external hard drive, a 1g flash memory drive and my Nokia N95.  None of them register in Places.

When I plug in my Nokia N95 it responds to my PC by asking if I want to transfer data or not.  Nothing happens on my PC.  

It recognises an external SD card.

I've been running Ubuntu 8.04 since it was released last year with no major problems so far.

Any thoughts?

---

### Post by kanikilu on 2009-03-06
After plugging a flash drive in, can you post the output of:

```
lsusb
```

and:

```
dmesg | tail -n 20
```

---

### Post by criptonite on 2009-03-06
Do I type that in to the command line of the terminal and hit enter?

---

### Post by criptonite on 2009-03-06
Ah, yes.  Sorry, I was raised on Windows which taught me how not to use my brain.

After lsusb

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 007: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader

Bus 001 Device 006: ID 0a81:0203 Chesen Electronics Corp. Mouse

Bus 001 Device 001: ID 0000:0000  


after dmesg | tail -n 20

[ 4913.231417] usb 2-7: new high speed USB device using ehci_hcd and address 39

[ 4913.334394] usb 2-7: device descriptor read/64, error -71

[ 4913.538365] usb 2-7: device descriptor read/64, error -71

[ 4913.741337] usb 2-7: new high speed USB device using ehci_hcd and address 40

[ 4913.844321] usb 2-7: device descriptor read/64, error -71

[ 4914.048290] usb 2-7: device descriptor read/64, error -71

[ 4914.251273] usb 2-7: new high speed USB device using ehci_hcd and address 41

[ 4914.653199] usb 2-7: device not accepting address 41, error -71

[ 4914.755188] usb 2-7: new high speed USB device using ehci_hcd and address 42

[ 4915.157126] usb 2-7: device not accepting address 42, error -71

[ 4987.258741] usb 2-7: new high speed USB device using ehci_hcd and address 43

[ 4987.361725] usb 2-7: device descriptor read/64, error -71

[ 4987.565695] usb 2-7: device descriptor read/64, error -71

[ 4987.768672] usb 2-7: new high speed USB device using ehci_hcd and address 44

[ 4987.871653] usb 2-7: device descriptor read/64, error -71

[ 4988.075622] usb 2-7: device descriptor read/64, error -71

[ 4988.278601] usb 2-7: new high speed USB device using ehci_hcd and address 45

[ 4988.680532] usb 2-7: device not accepting address 45, error -71

[ 4988.782521] usb 2-7: new high speed USB device using ehci_hcd and address 46

[ 4989.184459] usb 2-7: device not accepting address 46, error -71

---

### Post by kanikilu on 2009-03-06
According to this FAQ: [http://www.linux-usb.org/FAQ.html#ts6](http://www.linux-usb.org/FAQ.html#ts6)

I would probably start by trying:

```
sudo rmmod ehci-hcd
```

If that doesn't work, check the other suggestions listed on that page.

There's an old kernel bug that may be related :?:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273)

---

### Post by criptonite on 2009-03-08
Well, with no input from me, my PC has started to recognise all the USB ports again.  Hmmm, just one of those mysterys.

Anyway, thanks for your help anyway.  Forums rock!

---

### Post by nwadams on 2009-03-15
mine isn't fixed if i rmmod ehci-hcd 
it says the same errors with uhci-hcd (which is usb support so i can't remove that)

---

