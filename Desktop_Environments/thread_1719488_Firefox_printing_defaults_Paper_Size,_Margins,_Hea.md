---
title: "Firefox printing defaults: Paper Size, Margins, Header/Footer"
date: 2011-04-01
forum: Desktop Environments
---

### Post by urobb on 2011-04-01
I have searched High and Low for the answer to this, has anyone figured out how to wrangle Firefox print settings in Ubuntu 10.04.1 ?

I work for a record shop in Long Beach, CA.  We're an independent record store, it's only fitting that we use an open source Linux distro instead of Windows for our Point of Sale workstations.  I have been trying to do this for years now.  The ONLY hangup I've hand in making this happen is the (quirky?) print settings in Firefox.  I just need it to always select the Receipt printer by default, with the appropriate paper size, margins, and header & footer info (blank, blank, blank...)

We run a web based Point of Sale software, and need to print receipts to a local Thermal Reciept Printer, and also Letter sized documents to a Network Printer.  Getting both printers working was a breeze thanks to all the hard work from the kind folks behind Ubuntu, thank you.

I have spent countless hours messing with about:config settings with successful results, but for some reason they do not seem to stick after the browser is closed.  Here is what I have done that makes a successful print:

set all these empty:
print.printer_Receipt.print_footer*
print.printer_Receipt.print_header*

set these to 0:
print.printer_Receipt.print_edge_*
print.printer_Receipt.print_unwritable_margin_*

set these to taste:
print.printer_Receipt.print_margin_*

I am still terribly confused about forcing the Receipt printer to use the correct paper size.  These printer specific settings seem to work fairly consistently when opening print dialog manually, but using javascript: window.print() seems to bypass the printer specific settings.  All of these about:config settings don't seem to stay set permanently and I don't know what is causing the reset, but I think it happens as I'm using the page setup dialog.  I can't count on my co-workers leaving this stuff alone!  I'm just baffled, and I would be very grateful if anyone can offer any advice!

Can anyone demystify the about:config configuration file or offer me any advice on how to make Firefox remember settings on a per-printer basis?

This issue just seems like a silly reason for us to keep using our godforsaken Windows 2000 workstations and switch to Ubuntu.  Imagine how happy everyone here would be??!!!!

---

### Post by gtmarks on 2011-07-29
In about:config is the item print.save_print_settings set to "true"?

---

### Post by wyliecoyoteuk on 2011-08-21
I had the problem that the default paper size kept resetting to letter, when I wanted A4.
I solved by entering about:config in the menu bar, and searching for letter
I got 5 results, and changed them all to A4, problem solved.

print.postscript.paper_size;A4
print.print_paper_name;A4
print.tmp.printerfeatures.CUPS/Oki-Okipage-12i.paper.3.name;A4
print.tmp.printerfeatures.Oki-Okipage-12i.paper.3.name;A4
print.tmp.printerfeatures.PostScript/default.paper.3.name;A4

---

