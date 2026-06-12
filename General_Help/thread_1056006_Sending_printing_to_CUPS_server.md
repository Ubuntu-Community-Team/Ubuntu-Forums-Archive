---
title: "Sending printing to CUPS server"
date: 2009-01-31
forum: General Help
---

### Post by reler on 2009-01-31
OK, dumb newbie question, and it's perhaps not just an Ubuntu question, though you'll see why I am asking it here ! (Mixed software sometimes makes it difficult to know where you *should* ask questions !)

I have a router with an Ubuntu 8.10 SERVER installation with CUPS 1.3.9 on it and an old laser printer attached to its parallel port. The other machines attached to it are an OpenSUSE 11.0 box and a Windows XP Home laptop.

The Ubuntu machine has its MAC address programmed in to the router so that it always gets the same IP address. In the /etc/hosts file on the SUSE box, this address is allocated to a host name of psvr. Using the URL of *[http://psvr:631/](http://psvr:631/)* I can access the CUPS interface and I can see the printer definition. I can get it to print a test page successfully.

What I can't do is get printing from either of the client boxes to be accepted by the Ubuntu box.

In each case, I think that the problem is how the printer is defined to the client.

I have looked at this page: *[https://help.ubuntu.com/8.10/serverguide/C/cups.html]("https://help.ubuntu.com/8.10/serverguide/C/cups.html")*, but what none of the doc explains in a way that I can understand is how to define the printer on the client machines.

The nearest that I have come to success is on the XP laptop where the "internet port" for the printer that I have defined is shown as:
  *http:/192.168.x.xxx:631/printers/NameOfCUPSPrinter*

Sending a test page seems prompts this message on the CUPS LOG: 
  *Missing printer-uri, job-uri, or ppd-name attribute!*

The definitions on the SUSE box are less familiar to me, but trying to emulate the Windows set up by defining a CUPS "Network Printer" gives nothing on the log. All I get under "status" is:
  *Paused: /usr/lib/cups/backend/lpd failed*

I suspect that there may be issues to do with security but I am not an experienced enough Linux user to know about or understand these.

What I really want is something that picks up where the server doc leaves off. It just assumes that you know about these things. Sorry, I don't and I cannot find it !

For example, the CUPS web interface page for the printer I have defined shows a line that says:
  *Device URI: parallel:/dev/lp0 *
but this does not seem to fit in any of the definition fields on the clients. Where does this go ?

Sorry if this is against protocol because it's a cross-Linux/Windows question, but I have to start somewhere and hope that somebody here can point me in the right direction !

With thanks in anticipation,

Reler

---

### Post by cmnorton on 2009-01-31
Given the printer is connected to a server, you should be able to connect to it from either the Linux or windows client using the standard hp jet protocol. You can define it on the Ubuntu server side. 

I am used to our Linux servers running X and then using the CUPS web interface. The protocol is socket://ip-address/shared-printer-name. You would need to share this printer using SAMBA for the Windows client. 

For Linux to Linux, you can do the same thing.

Here are some examples from /etc/cups/printers.conf,where the names and IP addresses are replaced for display here.

<Printer pp0>
Info Data Products Line Printer
Location Info Tech Lab
DeviceURI socket://some-ip-addr:10001
State Idle
StateTime 1213098449
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

Note the port. This is because the NetPrint print server uses that port. Most of the time, especially for HP printers, the port will be 9100.

Here is one in my office. My Kubuntu workstation connects to a printer defined on an XP workstation system, which is different than if it were on an XP server:

<DefaultPrinter lp>
Info HP LaserJet 1320
Location my-office
DeviceURI smb://OurDom\login-name:my-password@OURDOMAIN/WSNAME/cmn_lp
State Idle
StateTime 1223561097
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

Please note I did not have to connect via SAMBA for this one. This printer is defined and shared out on a true domain controller, not an XP workstation.

<Printer labels_lp>
Info Hp Laserjet 4200
Location DP 4200
DeviceURI socket://our-domain-controller-ip:9100
State Idle
StateTime 1211988489
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by reler on 2009-02-05
Hi - thanks for getting back. Sorry it's taken me so long.

You'll have to bear with me because I speak Linux s-l-o-w-l-y !

> **cmnorton said:**
> Given the printer is connected to a server, you should be able to connect to it from either the Linux or windows client using the standard hp jet protocol. You can define it on the Ubuntu server side.

Ummm ... it's actually an old brother HL-1660 but I guess it's a kind of lookalike HP Laserjet, so does that last bit still hold good ?

> **cmnorton said:**
> I am used to our Linux servers running X and then using the CUPS web interface. The protocol is socket://ip-address/shared-printer-name. You would need to share this printer using SAMBA for the Windows client.

For Linux to Linux, you can do the same thing.

Here are some examples from /etc/cups/printers.conf,where the names and IP addresses are replaced for display here.

Well, Linux-Linux is the more important thing at the moment. I'll save Samba for another day ! 

But meantime, let me just slow it down a moment ... sorry, but like I said, I'm pretty much a newb, especially on the server side.

I assume that you mean /etc/cups/printers.conf on the server, right ? (My philosophy is to NEVER miss an opportunity to ask a REALLY stupid question !)

> **cmnorton said:**
> <Printer pp0>
Info Data Products Line Printer
Location Info Tech Lab
DeviceURI socket://some-ip-addr:10001
State Idle
StateTime 1213098449
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

Note the port. This is because the NetPrint print server uses that port. Most of the time, especially for HP printers, the port will be 9100.

NetPrint ? Wozzat ?

> **cmnorton said:**
> Here is one in my office. My Kubuntu workstation connects to a printer defined on an XP workstation system, which is different than if it were on an XP server:

<DefaultPrinter lp>
Info HP LaserJet 1320
Location my-office
DeviceURI smb://OurDom\login-name:my-password@OURDOMAIN/WSNAME/cmn_lp
State Idle
StateTime 1223561097
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

OK, hang on ! Maybe you're referring to the /etc/cups/printers.conf file on the **client** machine instead !

> **cmnorton said:**
> Please note I did not have to connect via SAMBA for this one. This printer is defined and shared out on a true domain controller, not an XP workstation.

<Printer labels_lp>
Info Hp Laserjet 4200
Location DP 4200
DeviceURI socket://our-domain-controller-ip:9100
State Idle
StateTime 1211988489
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

OK, I'm grateful that you have given me a lot of detail but it doesn't quite fit my understanding of this. So let me see if I have this right:

- I need to define the server's printer on my client in its /etc/cups/printers.conf (and I see that I do have one which has my unsuccessful attempts at making the definition through the gui that Gnome provides).

- If that's right, it seems to me that the crucial part of it is the DeviceURI line. What goes there ? Like I said, the CUPS interface tells me that this is **parallel:/dev/lp0** for the laser attached to the server. Presumably I have to prefix that with some kind of address e.g. 192.168.x.xxx, right ? Maybe include a port number and even a userid & password ? Would it look something like this: 
   ```
DeviceURI http://192.168.x.xx:631\login-name:my-password@192.168.x.xx/parallel:/dev/lp0
```

- I am obviously not well up on URI formats, so I am not sure if this is supposed to include "http" or what. Not familiar with "socket" or "smb", but then I'm an emigrant to Linux via mainframes and Windoze.

THESE are the things I don't "get". And I can't find clear reference material.

If you haven't exactly pointed me in the right direction, you have at least saved me from charging off in completely the wrong direction ! So, I'm very grateful. If we can just straighten out some of the links missing in my knwledge (or at least find out where I can do that), I think I'll be well on my way.

Thanks for your help.

Reler

---

### Post by reler on 2009-02-12
Buuuump !

---

