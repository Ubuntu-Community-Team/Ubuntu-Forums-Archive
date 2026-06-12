---
title: "Installing Canon MF4370dn on ubuntu 9.10"
date: 2009-11-05
forum: Desktop Environments
---

### Post by boosis on 2009-11-05
Hi all.

I have been trying to install Canon MF4370dn on my ubuntu 9.10 connected via USB for the last couple of day. I managed to get it working as a scanner but I'm not having any luck with printing.

That's what I did so far. Downloaded the linux drivers from Canon's web site (Asia). When I connect the printer ubuntu recognizes the printer and asks for the drivers. I chose the correct driver and it installes both printer and fax drivers. But when I try to print a test page nothing happens. on the printer properties window status changes from Idle- Printer is now online to processing and then goes back to Idle. No print comes out.

I checked the log files when I print the test page and only thing I see is in cups access log showing 
[B]localhost - - [05/Nov/2009:20:40:18 +0000] "POST /printers/Canon-MF4360-4390-(UFRII-LT) HTTP/1.1" 200 152979 Print-Job successful-ok

[/B]Also when I swtich off and on the printer I get the following messages from messages log.

[B]Nov  5 20:41:38 ubd-1 kernel: [61909.240013] usb 2-1: new high speed USB device using ehci_hcd and address 6
Nov  5 20:41:38 ubd-1 kernel: [61909.411145] usb 2-1: configuration #1 chosen from 1 choice
Nov  5 20:41:38 ubd-1 kernel: [61909.417341] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x04A9 pid 0x26EC
Nov  5 20:41:38 ubd-1 kernel: [61909.422699] usblp1: USB Bidirectional printer dev 6 if 2 alt 0 proto 2 vid 0x04A9 pid 0x26EC
Nov  5 20:41:39 ubd-1 kernel: [61910.542339] usb 2-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Nov  5 20:41:39 ubd-1 kernel: [61910.542363] usb 2-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Nov  5 20:41:41 ubd-1 udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Canon-MF4360-4390-(FAX)[/B]
So technically everything seems to be working :) only thing is there is no print!

Can someone help me with this?

Thanks
B

---

### Post by raidensix on 2009-11-05
Which version of the Canon drivers are you using? I had the same problem when I was using 1.9. Rolling back to 1.8 solved it for me.

---

### Post by boosis on 2009-11-05
I am using 1.90. 
Where did you find version 1.80 from?

---

### Post by raidensix on 2009-11-05
I don't remember the website I got them from but you can try this: [http://fr.software.canon-europe.com/software/0031081.asp](http://fr.software.canon-europe.com/software/0031081.asp) 

It's the Canon french site.

---

