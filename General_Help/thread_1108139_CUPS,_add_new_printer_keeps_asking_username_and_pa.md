---
title: "CUPS, add new printer: keeps asking username and password."
date: 2009-03-27
forum: General Help
---

### Post by Jeandré on 2009-03-27
Old Ubuntu 6.06 LTS setup.

Added an HP LaserJet 5L printer. 

Under System, Administration there isn't a Printers.

Saw at [_CUPSDocumentation_]("http://www.linuxfoundation.org/en/OpenPrinting/Database/CUPSDocumentation") to go to [_http://localhost:631/admin_]("http://localhost:631/admin"). From there I selected add printer, but at the point where it asks username and password that dialog just keeps coming back up after Enter/OK. No error message. Both username and password (of primary/root user (has lpadmin rights)) typed in correctly, and I'm logged in as that user.

---

### Post by HermanAB on 2009-03-27
That is oooold... It may be worth installing a fresh copy of Ubuntu.  The latest printer wizard works very well.  Otherwise, you need to install the printer manually - the foomatic web site could possibly get you going:
[http://sourceforge.net/projects/foomatic/](http://sourceforge.net/projects/foomatic/)

and maybe these tricks will help:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

but really, there is a good reason why the new system-config-printer wizard was created!

---

### Post by Jeandré on 2009-04-10
The PC is old and can barely handle 6.06 LTS. My new PC only has USB ports so no where to plug in the printer.

Anyone know how to get past the username and password dialog?

---

