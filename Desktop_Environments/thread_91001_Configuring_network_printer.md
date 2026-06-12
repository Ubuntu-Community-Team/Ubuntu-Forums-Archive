---
title: "Configuring network printer?????"
date: 2005-11-16
forum: Desktop Environments
---

### Post by GolfBall on 2005-11-16
Maybe this belongs in the network folder - I don't know.  Anyway, i am new to Linux.  I love Ubuntu but I am having difficulty configuring my printer.  I have an HP 932C DeskJet printer connected to a Linksys network printserver (PSUS4).  Everything connects through a router.  Everything works fine under Windows XP.  Under Windows XP I have the printer configured to print to a standard TCP/IP port and I specify the IP address of the Linksys print server.  With Ubuntu Linux, the only place I can find to set an IP address for printing is if I choose an HP JetDirect network printer.  If I choose this option, and I have tried it numerous times, it will print about 3/4 of a page and hang the printserver which hangs my home network until I unplug and then replug the LinkSys printserver to reboot it.  I have selected the 932C driver that Linux suggested.  Any suggestions on the proper way to configure this setup under Ubuntu Linux would be appreciated.  Thanks.

---

### Post by saultpastor on 2005-11-16
I don't know anything about the linksys network printer setup.  But my printer (932c) is served through another linux box on my home network.  All I did in Ubuntu is System >> Administration >> Printing  And selected Global Settings from the menu and checked Detect Lan Printers. It picked it up perfectly. 

I have no idea how to setup through a print router or whatever that is, So this may be of no help at all.

---

### Post by GolfBall on 2005-11-16
saultpastor - Thanks for the suggestion.  I just tried to detect LAN pinters.  Unfortunately it didn't find anything so I am still "up the creek".  I just wish that I could find a straight forward way to tell it to send the print info to a TCP/IP address.  In windows it is set up to use port 9100 and then I specify an IP address and everything works.  Under Ubuntu, if I select the HP JetDirect option and specify port 9100 and the IP address then it tries to print for a while.  It hangs the print server box after printing part of a page and it actually hangs my whole home network until I reset the print server.  So, it almost works.  I suspect that the HP JetDirect option is not the way to go, but I don't know any other way that gives me the choice to select port 9100 and then give it an IP address.

---

