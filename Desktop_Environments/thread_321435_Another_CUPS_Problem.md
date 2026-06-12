---
title: "Another CUPS Problem"
date: 2006-12-18
forum: Desktop Environments
---

### Post by ctcljavarox on 2006-12-18
Hey,
I just set up two linux boxes, both running Ubuntu Dapper.  I've got an Epson printer on machine A.  I wanted to remotely print from machine B to machine A.  So I set it all up by modifying the configuration files (I've already tried the GUI).

From the threads on this forum, it sounds as if CUPS 1.2.2 is buggy but I think that's just me.

When I print from machine B, it says "Gutenprint - 94%" or something, and then "Waiting for job to finish..."

Meanwhile on machine A, I see absolutely no activity.  lpstat -t never turns up anything either.  But the print job does show up in the logs, but with an Unknown number of pages.

Can anyone give me a hand?
Thanks!

---

### Post by ctcljavarox on 2006-12-19
For the record, I solved the problem!

Apparently, the "Print Test Page" in the Printers administration dialog sends a raster-based file of MIME type application/vnd.cups-raster or something to the remote print server.  And somehow, that server can't process it, so it says "Gutenprint printed 0 bytes".

Anyways, everything else (lpr, firefox, openoffice) works file so I'm happy with that =]

---

