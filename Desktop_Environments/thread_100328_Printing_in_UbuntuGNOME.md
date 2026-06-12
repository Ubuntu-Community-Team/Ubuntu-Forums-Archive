---
title: "Printing in Ubuntu/GNOME"
date: 2005-12-07
forum: Desktop Environments
---

### Post by WebDrake on 2005-12-07
Hello all,

This is perhaps a *very* dumb question; but it's about a part of Linux I have never dealt with before: printing.

I've set up several CUPS printers using the nice GNOME System -> Administration -> Printing wizard, but I don't know how to select between them when printing a document (say, from Adobe Acrobat Reader).  The only option I get for a printer is /usr/bin/lp ; no automatic choice or selection as in Windows XP.

So... Umm... what do I do? :rolleyes: 

The second problem, but a minor one, is that I'd like to be able to rename the printers: currently they're listed as "Color LaserJet 3700" or whatever, but I'd like to be able to change that name, and I haven't found out how to.  Altering the Description in the printer Properties doesn't work (and isn't preserved by the system).

Thanks in advance for all advice! :-)

       -- Joe

---

### Post by schilcha on 2005-12-07
[QUOTE=WebDrake]
I've set up several CUPS printers using the nice GNOME System -> Administration -> Printing wizard, but I don't know how to select between them when printing a document (say, from Adobe Acrobat Reader).  The only option I get for a printer is /usr/bin/lp ; no automatic choice or selection as in Windows XP.
[/QUOTE]

In Acrobat, you can edit the print-command. Just make it read "/usr/bin/lp -d YourPrinterName" (-d for destination). In case you try lpr, use the -P flag ("lpr -P YourPrinterName"). You can define a default printer by setting the PRINTER environment variable (e.g. in /home/you/.bashrc).

I have no clue, why acrobat uses such a strange printer-dialog. It's such a convenient app in most other aspects. Other apps, such as firefox allow printer selection via a drop-down-list.

For your second problem: Never tried that...

Anyways,
Good Luck

---

### Post by WebDrake on 2005-12-07
Many thanks! :-)

I can save the rename problem for later, it's hardly the most urgent thing in the world... :rolleyes:

---

