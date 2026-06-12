---
title: "printing to a CUPS print server"
date: 2005-06-23
forum: Desktop Environments
---

### Post by danjmw on 2005-06-23
hey all,

I'm having a little difficulty connecting to a printer off a print server running CUPS.  This may be a piece of cake but I'm a bit of a new be on Linux systems.  The server is named PSERVER and the printer is named QSG_PRINTER.  I've tried the following in the printer gui when set to Network Printer: CUPS Printer:

[http://192.168.0.98:631/printers/qsg_printer](http://192.168.0.98:631/printers/qsg_printer)
ipp://192.168.0.98:631/printers/qsg_printer
ipp://192.168.0.98:631/qsg_printer

These settings don't connect to the printer.  Am I not identifing the printer correctly?

Appreciate the help.

Dan

---

### Post by Alexander Kirillov on 2005-06-23
[QUOTE=danjmw]hey all,

I'm having a little difficulty connecting to a printer off a print server running CUPS.  This may be a piece of cake but I'm a bit of a new be on Linux systems.  The server is named PSERVER and the printer is named QSG_PRINTER.  I've tried the following in the printer gui when set to Network Printer: CUPS Printer:

[http://192.168.0.98:631/printers/qsg_printer](http://192.168.0.98:631/printers/qsg_printer)
ipp://192.168.0.98:631/printers/qsg_printer
ipp://192.168.0.98:631/qsg_printer

These settings don't connect to the printer.  Am I not identifing the printer correctly?

Appreciate the help.

Dan[/QUOTE]
 ipp:// protocol is for printing to a directly networked printer (i.e., printer wiht a network card). If you want to use a remote cups server, change ServerName line in /etc/cups/client.conf

Note: then your own machine CUPS server will not be used at all. If you want to use both, you will need to enable browsing on remote CUPS server - so that it allows you to get the list of its printers. This is something I have only vague ideas about.

---

