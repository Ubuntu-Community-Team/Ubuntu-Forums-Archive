---
title: "Cannot scan for the life of me"
date: 2010-02-15
forum: Desktop Environments
---

### Post by nikkkko on 2010-02-15
Upgraded from 9.04 to 9.10 and now cannot scan from my wireless HP F4580 all-in-one machine.

I can ping the printer, I can print to the printer, I can see the webgui of the printer, I can snpwalk the printer but I cannot scan from the printer.  This is because the printer has no uri. But when I run :

hp-makeuir <ip address>

I get :

"error : device not found"

Eventually I plugged in the printer by usb and guess what?  I still can't scan.  So I then did:

hp-makeuri 002:010

being the usb bus and device id and I still get 

"error : device not found" 

Half a day in the hole, has anyone else trodden this path and found the answer?

Thanks

---

### Post by night_fox on 2010-02-15
Use CUSS!

Common Unix Scanning System

[Sorry, i dont know the answer, and this wont help cos its a joke]

---

### Post by nikkkko on 2010-02-15
OUch !

---

### Post by night_fox on 2010-02-15
Sry, I had to say it!

---

### Post by nikkkko on 2010-02-15
[rant]I HATE our HP printers.  I hate the fact that our laserjet costs more to stock on powder than it does to buy a new printer.  I hate the fact that to install the driver for the wireless deskjet, (in windows, yes we have a windows box on the network), you have to download 70mb of garbage and it still doesn't work. I hate the HP-Toolbox which doesn't show the installed printers and I hate the fact that I've wasted almost a whole day pulling out what's left of my hair to scan a single page of A4.[/rant]

---

### Post by SoFl W on 2010-02-15
I had a different problem with an HPScanjet.  It found the scanner but XSANE would close after the scanner scanned but before it processed the image.

Someone recommended that I use a previous version of libsane.  I don't know if this will help you, but it might lead you to a better answer.  [**LINK**]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476")

---

### Post by nikkkko on 2010-02-15
> **SoFl W said:**
> Someone recommended that I use a previous version of libsane.  I don't know if this will help you, but it might lead you to a better answer.  [**LINK**]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476")

I'm pretty sure it's not a libsane problem. The problem is that I can't get the uri of the printer.  I used to be able to in 9.04, but now I can't and I don't know why.

---

### Post by stuarttaylor on 2010-04-06
I'm also having trouble getting the scanner detected. I think I've narrowed it down to the printer not being detected when you plug it in via USB. lsusb doesn't show any device listing. I'm running out of ideas on how to get the system to list the device.

---

