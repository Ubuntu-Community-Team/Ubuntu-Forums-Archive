---
title: "CUPS setup the same on different subnets?"
date: 2006-10-31
forum: Desktop Environments
---

### Post by bazzer on 2006-10-31
Hi all
Got a small problem I don't understand what to do with. Essentially, I'm putting an install script together to configure a PC with all the applications and configurations to make a 'kiosk'. The install will be used by many people over a wide geographical area and I don't want to have to visit these places personally. So the install must be done automatically.

I'm having trouble getting my head around what to do with the printing. So far, I've got this:
[INDENT]lpadmin -E -p kiosk-printer -v socket://10.0.4.100/printers/kiosk-printer -P /usr/share/cups/model/cups-included/HP/laserjet.ppd -u allow:all
accept kiosk-printer
lpadmin -d kiosk-printer
cupsenable kiosk-printer[/INDENT]
Which works. But - I think we're going to have different IP ranges for different kiosk environments. So one printer will be 10.0.4.100, another location's printer will be 10.0.5.100 and so on.
So the question is this - how can I make the lpadmin command look for a printer with a 10.0.whatever.100 IP address?

All ideas welcome! :)

---

