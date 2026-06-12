---
title: "Connect to D-Link DP-301P+ Ethernet Print Server"
date: 2007-10-21
forum: Desktop Environments
---

### Post by ogoforth on 2007-10-21
I have a small home network. I recently installed Ubuntu 7.10 on an old Compaq P3.  I want to be able to print to my LaserJet 5 connected to the print server and network.  The setup instructions don't include any Linux directions.  Can any one provide assistance?

ThanX,
ogoforth
[email]ogoforth@gmail.com[/email]

---

### Post by liangfok on 2007-11-15
Browse to [http://localhost:631](http://localhost:631) and click on "Add Printer".  This will walk you through a series of steps where you can configure your printer. Specifically, when it asks you for the device, choose "IPP", then specify the address as "socket://192.168.1.10" (assuming you haven't changed its default IP address).

---

### Post by scotoma on 2008-02-18
I had to choose lpd/lpr and set the location to lpd://192.168.0.10

p

---

