---
title: "Printer to Router - Can it be done?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by El Guapo on 2006-07-19
I am trying to set up my printer (HP Officejet 6310) at home.  The printer has an ethernet port on it and I want to hook it up to my router and then use it from my Ubuntu box and Windows laptop.  The Ubuntu box uses ethernet to hook to the router and the laptop uses a wireless connection.

I have read about Samba and cups, and it all seems to point to having the printer hooked directly to a machine instead of a router.  Can I print over a router in linux?  I am  assuming I can since the printer came with driver support for Windows and Mac.  Can anyone point me to a resource to get started with this?

I have never set up a network before, but I am not afraid of learning how.  Is this what I need to do?

---

### Post by tturrisi on 2006-07-19
[Check Here]("http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=us&dlc=en&product=1119598&lang=en&")

---

### Post by llamakc on 2006-07-19
Not only can it be done but you'll be finished with hooking printers up directly once you get it wired. Good luck.

---

### Post by El Guapo on 2006-07-19
I had read my manuals before I posted this question.  The manuals work very well if I am running a Windows machine or a Mac machine.  They have software installation CD's for both OSes but not for linux.

What do I need to do in order to find the printer?  I tried just plugging it in and looking for it under the printers section.  I find one and try to print but nothing happens.  Do I need some sort of network set up first?  I even tried from my Windows laptop over the wireless connection and it cannot find it either.  Do I assign an ip address to it or something?

Please help...

---

### Post by llamakc on 2006-07-19
ON the printer side you'll need to follow the printer's documentation to make sure it is acquiring an IP from your router (assuming that is your setup).

On Ubuntu, you just need to add it in the SYSTEM | ADMINISTRATION | PRINTING window. The catch is knowing what its IP is and what syntax to use when adding it.

For example, my Dell 1710n I have connected via JetDirect and I have to use the LaserJet Series PCL 6 CUPS driver to get it to work.

In the 'add printer' dialog you choose 'network printer' and go from there.

---

### Post by El Guapo on 2006-07-19
My printer has an IP address, I know what it is.  I know its hostname, MAC address, IP address and all sorts of stuff.  From the printer side, I believe it is working properly.

My network options are: CUPS, Windows, UNIX, and HP JetDirect.  I have tried both CUPS and HP JetDirect without much luck.  When I try HP JetDirect I am asked for a host and a port.  Where do I get this information?  I tried using the Hostname info from the printer and when I try to print a test page it stops it, which is better than before when it would just say it is printing forever.  

When I try the CUPS method and use the ip address of my printer in the URI field it again stops immediately.  Is there a log of errors telling me why these print jobs are being stopped?

When I go to set it up I use the HPLIP driver as suggested by the LinuxPrinting.org website.  Although is has two drivers listed there, how do I know what I am choosing?

---

### Post by El Guapo on 2006-07-20
I figured it out!!! \\:D/ 

Here is what I did:

From another post: [http://www.ubuntuforums.org/showthread.php?t=184838](http://www.ubuntuforums.org/showthread.php?t=184838) I followed the instructions to install the hpij and hpoj drivers.  In this process I noticed the terminal say that there was a configuration file that was not used.  I found this file here /etc/init.d/hpoj and ran it from the command line with the following command:

```
sudo /etc/init.d/hpoj setup
```

From there I followed the instructions and added the IP address when it came to it.  Then when I went to add a new printer using System -> Administration -> Printing and my printer was found as a local printer.  There was no need to mess around with any details in there and now it works like a charm!

I hope this helps anyone else that is looking to install an HP OfficeJet printer.

---

### Post by llamakc on 2006-07-20
Congratulations!

---

