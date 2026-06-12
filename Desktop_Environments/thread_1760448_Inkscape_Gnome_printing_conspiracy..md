---
title: "Inkscape Gnome printing conspiracy."
date: 2011-05-16
forum: Desktop Environments
---

### Post by Sciezyna on 2011-05-16
Ubuntu 10.04 LTS, Gnome 2.30.2 (up to date), Inkscape 0.48 (tried 0.47).

I searched the net decently for the last week found few 'briliant' answers to no avail.

I have Epson printer NX125. It prints well from all (eg. GIMP, Adobe Reader, Scribus,+) applications but one - Inkscape. What more Inkscape trashes the print queue 1-2 seconds after sending a print job, leaving Printer state in:

Idle '/usr/lib/cups/filter/pips-wrappe failed'

which is annoyingly difficult to clear out (delete and reinstall the printer). System Diagnose does not make any sense, suggest turning on 'Sharing' - but the printer has that tick box ticked.

I also have a draft printer, HP LaserJet 6mp, and Inkscape prints to this printer with no problems.

Summary:

Inkscape does not print and trashes the Epson NX125 queue.
Inkscape prints to the HP LJ 6mp.

All other apps (GIMP, Scibus ++) print to both printers.
None will print to the trashed Epson NX125 queue.
After I 'Duplicate and delete' the NX125 the above Status is cleared and printing is ok till Inkscape.

It seems that Inkscape and the NX125 have an issue and I was not able to find out what it is. Because of the above the culprit is Inkscape.

My last action was to compile and install Inkscape on my system - does not make any difference.

From the net I know that there are other printers with that same problem.

If a sollution is not available I would be satisfied with an answer from the most experienced and knowledgeable Linux users: 'Sorry we do not know.'

Meanwhile what I do is. Created something in Inkscape, save in .svg and .pdf. Open file in GIMP and print to the Epson. It is a sollution but an annoying one because I am using Ubuntu not Windows.

Thanks for comments.

---

