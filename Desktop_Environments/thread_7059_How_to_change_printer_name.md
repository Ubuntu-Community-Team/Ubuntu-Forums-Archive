---
title: "How to change printer name ?"
date: 2004-12-03
forum: Desktop Environments
---

### Post by beaufils on 2004-12-03
I more used to lprng than cups printing system, so my question
may be consider as a newbee one.

I want to use Ubuntu in an environment with a lot of
differents printer.

When I add them with the gnome-cups-manager installed in
Ubuntu I do not have the choice of what name I want to
give.

I want to be able to choose whatever name I want for my printer
just because it is easier to remember for me. I want thus to be able
to change the name of a printer.

Any ideas how to do that ?

---

### Post by JonAtkinson on 2004-12-06
Okay, I know that you can do this using the 'real' CUPS interface (the web-based one). It's at [http://localhost:631](http://localhost:631).

However, Ubuntu seems to do some form of restriction (see the red text at the top) on what you can do here. If you can figure out a way to disable this, then you'll be able to rename the printer under the "Manage Printers" section of the interface.

--Jon

---

### Post by mfranz on 2005-01-18
After configuring printers with the gnome tool, I wasn't able to change their names neither through the tool itself nor using the web interface: it asked me an administrative password but it doesn't seem to use sudo, so I wasn't able to enter printers configuration.
The only way I was able to do it, was by modifying the cups files:
In
/etc/cups/printers.conf
I changed
<Printer printer_name_set_by_gnome_2>
and
<DefaultPrinter printer_name_set_by_gnome_1>
with the names I wanted.
Then I renamed the ppd configuration files in
/etc/cups/ppd
using the names I chose for my printers in /etc/cups/printers.conf

---

