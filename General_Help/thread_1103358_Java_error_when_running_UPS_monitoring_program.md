---
title: "Java error when running UPS monitoring program"
date: 2009-03-22
forum: General Help
---

### Post by demlasjr on 2009-03-22
Hi everybody and thank fron your great community and for all helps.
I installed 2 days ago an UPS for my pc. Was difficult to install because appear problem with java, but I reinstalled java and everything was fine. But the problems is I need to refresh everytime the the agent with 
> sudo ./agent restart

If not, I get this error:

> Mar 22 13:01:15 server kernel: [  139.540068] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Mar 22 13:01:15 server kernel: [  139.540085] usb 3-1: USB disconnect, address 6
Mar 22 13:01:16 server kernel: [  139.760061] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 13:01:16 server kernel: [  140.330047] usb 3-1: new low speed USB device using uhci_hcd and address 8
Mar 22 13:01:16 server kernel: [  140.512039] usb 3-1: configuration #1 chosen from 1 choice
Mar 22 13:01:16 servers kernel: [  140.571098] hiddev96hidraw2: USB HID v1.00 Device [Cypress Semiconductor USB to Serial] on usb-0000:00:1d.1-1


This error repeats all time if I don't use restart agent function. I searched in all google but no resolve for this errors. Well. Then everything is going fine, but if I want to start de monitoring software
(sudo ./monitor), this software start and working perfect, but in console I get an annoying error and is impossible to check other messages and error because I get 1 message per second:

> Mar 22 14:47:29 server kernel: [ 6513.291845] usb 3-1: usbfs: process 10670 (java) did not claim interface 0 before use                                 
Mar 22 14:47:30 server kernel: [ 6514.483632] usb 3-1: usbfs: process 10670 (java) did not claim interface 0 before use                                 
Mar 22 14:47:31 server kernel: [ 6515.501509] usb 3-1: usbfs: process 10670 (java) did not claim interface 0 before use                                 
Mar 22 14:47:33 server kernel: [ 6516.689220] usb 3-1: usbfs: process 10670 (java) did not claim interface 0 before use                                 
Mar 22 14:47:34 server kernel: [ 6517.674189] usb 3-1: usbfs: process 10670 (java) did not claim interface 0 before use               

Is any possibilities to resolve this error ? Or simple, to exclude this error from syslog ?

---

### Post by demlasjr on 2009-03-22
anybody ? 40 mins passed and no views of this topic :(

---

### Post by micahsdad1402 on 2009-04-25
Did you get a solution to this one?
 
I have the same issue (running winpower)!

---

### Post by demlasjr on 2009-04-25
> **micahsdad1402 said:**
> Did you get a solution to this one?
 
I have the same issue (running winpower)!


No....it was annoying for my server. So I changed my OS to Debian Lenny. I don't have any problem now, everything working perfect and more faster. Too much problems in Ubuntu :( Sad.

---

### Post by micahsdad1402 on 2009-04-25
I'm running Centos 4.

Perhaps I need to upgrade to centos 5.

I'll try and contact my UPS provider to see if they have an answer.

thanks anyway.

---

### Post by etapien on 2009-11-07
has anyone found a fix for this issue? I was experiencing the same on hardy and thought karmic would make a difference but i'm getting the exact same annoying behavior.

---

### Post by Shazaam on 2009-11-07
If your ups is made by APC install apcupsd and gapcmon with Synaptic.

Some links for you...
[http://www.apcupsd.org/](http://www.apcupsd.org/)
[http://www.networkupstools.org/](http://www.networkupstools.org/)

---

