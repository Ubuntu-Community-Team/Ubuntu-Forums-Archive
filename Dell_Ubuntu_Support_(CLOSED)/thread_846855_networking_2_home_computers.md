---
title: "networking 2 home computers"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Garyb1 on 2008-07-01
Hi, I Have 2 computers 1 is a Dell laptop with wi-fi and the other is a
dell desktop which has a hp5610 printer connected to it.
I have a Belkin wirless N router, the desk top is connected to it by hardwire and of course the lap top communicates by wireless. What i would like to do is share folders, files and print from my laptop to the printer that is connect to my desktop. Both computers have Ubuntu ultimate 8.04 installed on them. the name of my laptop is connie@connie-laptop it was connie-laptop but when i added the domain named workgroup the name of the comptuer changed, the same for my desktop it was gary-desktop now gary@gary-desktop.

My laptop ip is 192.168.2.4
My desktop is 192.168.2.2

broadcast address is 192.168.2.255
subnet mask 255.255.255.0
default route 192.168.2.1
primary DNS 192.168.2.1
secondary DNS 0.0.0.0
hardware address: 00:16:44:6D:FF:70 Laptop
hardware address: 00:0B:DB:CD:F7:E2 dessktop

I am new to Ubuntu but i have used it enough to know i want to stay with it, i like it very much i have set up every thing myself this is the last thing i need to do to make things complete. Please could someone out there take some time out of their day and help me or right a step by step procedure a dummy could follow. i have spent 2 days trying to get it to work with samba but i have failed to get it to work.

Thanks

---

### Post by bcom on 2008-07-02
Did some research on your question, here is what I found.  Please be sure to make a copy of the existing cupsd.conf file so you can revert to it if this doesn't work.

To allow other systems to connect to the CUPS server on the local system, you must instruct CUPS to bind to an IP address that the other systems can reach.  So, navigate to /etc/cups and once there, sudo gedit cupsd.conf.

Where it says: #Only listen for connections from the local machine.
Listen localhost:631, add Listen 192.168.2.2:631 on the next line.

Save and close the file.

Next issue the following command: sudo /etc/init.d/cupsys restart.  Anytime you change the cupsd.conf file you must restart the cupsys daemon.

You will have to install the printer on the laptop and in the printer settings enter something like lpd://192.168.2.2:631 or maybe just 192.168.2.2:631.

---

