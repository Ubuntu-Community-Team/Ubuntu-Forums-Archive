---
title: "Is anyone out there able to print to a network printer under Feisty?"
date: 2007-05-14
forum: Desktop Environments
---

### Post by RichardBronosky on 2007-05-14
I'm not talking a printer shared from another PC.  I want to start a discussion about printing to business grade laser printers/copiers with built-in ethernet.  There are WAY too many points of failure in the existing discussions about inkjets connected to windows computers share on networks.

I have a slew of HP Laserjets, Ricoh Multifunction Copiers, Toshiba Copiers, Canon Copiers, etc. that worked perfectly under Edgy.  Now, under Feisty, I tell it to print, but nothing comes out.  No errors in the GUI, or /var/log/cups/error_log.  In /var/log/cups/access_log I get:
```
localhost - - [14/May/2007:16:15:01 -0400] "POST /printers/LP138c HTTP/1.1" 200 125214 Print-Job successful-ok

```

I have no idea where to go from here.  Everyone else in my company who uses Linux uses CentOS, and the think I'm crazy for dealing with this.  All I can say is that I hate RPM, but I starting to hate this more.

---

### Post by Ateo on 2007-05-14
I have my printer plugged into an ASUS WL500gp access point which in turn makes it a 'networked' printer. So, with that said, yes, I can print from ANY of my 2 Feisty installs (one desktop/one laptop)  to this networked printer. 

Are you configuring it correctly?

/edit
Now that I think of it, this router does treat it like a window share so sorry for replying with uselessless. =)

---

### Post by starfry on 2007-05-15
Hello,

Yes I have an HP Officjet 7200 and can print to it just fine across the network. I can also use it as a scanner across the network too. Luckily, HP provide Linux drivers, etc, that make it work.

---

### Post by RichardBronosky on 2007-05-15
So, how did you set up the printer? I've tried:
[LIST=1]
[*]System>Administration>Printing
[*]New Printer [launches gnome-cups-add]
[LIST]
[*]Printer Type: Local or Detected Printer
[LIST=3]
[*]Use driver from [http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[*]Apply
[/LIST]
[*]Printer Type: Network Printer
[LIST]
[*]IPP Printer - URI: [http://confirmed_ip:631/ipp](http://confirmed_ip:631/ipp)
[LIST=3]
[*]Use driver from [http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[*]Apply
[/LIST]
[*]TCP/Socket, HP JetDirect - Host: confirmed_ip
[LIST=3]
[*]Use driver from [http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[*]Apply
[/LIST]
[/LIST]
[/LIST]

Unfortunately I get no prints.

Ahh! I tried this from my laptop several times on multiple printers over the past few weeks (multiple days, with reboots regularly).  But now, as I'm going through it again to get exact verbiage for this post... It works.  On every printer.  Both the Detected and Socket configurations work on each!  (I don't seem to have authorization for ipp)

I hate when this happens!

---

### Post by starfry on 2007-05-16
Hi, I installed HPLIP  [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/).  It just worked for me.

Of course this is for a suitable HP printer and, FWIW, it works via CUPS.

---

### Post by llamakc on 2007-05-16
I've always been fond of getting my printers (networked, local, and shared) working through [http://localhost:631](http://localhost:631) (the CUPS web interface).

Yes, I have no problem printing to two networked printers (Feisty clean install).

---

### Post by seamuso on 2007-05-16
printing/scanning with no problems to my HPC5180 via its built-in ethernet, also using the HPLIP which installed by default with feisty.

---

### Post by stanjam on 2007-05-16
I was able to get my HP OfficeJet 4215 running on a networked DLink network printer server by simply setting up the network printer under JetDirect options and simply putting in the IP address of the print server.  Works fine, though I am going to try the HP software mentioned in this thread.

---

### Post by tgm4883 on 2007-05-16
I can print to my Brother MFC-5440CN under feisty with minor setup (32-bit only, still working on 64 bit).  I can scan too.

---

### Post by Cotopaxi on 2008-02-18
tgm4883:

How did you manage to get your printer running? I have been working for one week now and I still don't mangage to get it printing!

---

### Post by tgm4883 on 2008-02-18
> **Cotopaxi said:**
> tgm4883:

How did you manage to get your printer running? I have been working for one week now and I still don't mangage to get it printing!

There are instructions on the brother website for printing.  Basically it involves going into the cups web interface and finding the correct port and such for the printer (I think mine was something like 531).  There should be more detailed instructions on the website listed in my sig

---

