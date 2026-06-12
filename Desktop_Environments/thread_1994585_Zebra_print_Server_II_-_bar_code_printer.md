---
title: "Zebra print Server II - bar code printer"
date: 2012-06-03
forum: Desktop Environments
---

### Post by jm2 on 2012-06-03
I just wanted to share a solution I figured out that didn't quite match with the other help I found on line.

Ubuntu 10.4 
I have bar code printer - Zebra. 
I have the bar code file already in ZPL format and just want to send it to the printer.

This printer has its own static ip address. I can ping it, so I know it's on the network.

System - Administer - Printers - Add printer
(This printer does not show up on printer listing - that's ok)
I choose Apple Socket / HPjet direct
Entered in the IP Address. xxx.xxx.xxx.xxx
Port: 9100

Printer type - Choose Generic
Drive - Choose Raw Queue

This worked like a charm for all the bar code printers I needed to install.
I didn't need the zebra.ppa at all.

---

