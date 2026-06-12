---
title: "Lexmark 6575 printer with CUPS"
date: 2009-05-25
forum: General Help
---

### Post by ianboag on 2009-05-25
I'd class my Linux staus as "advanced newbie"

I have one of these hooked up as a wireless network printer. It works fine off Windows machines.  A friend with a MacBook was visiting the other day - his machine found it, decided it was an LPR (LPD?) printer and also printed to it just fine.

localhost:631 on my eeePC (running Easy Peasy) brings up CUPS. Easy Peasy CUPS (to my surprise) is an Apple copyright product. Mac OS X is just Unix.

My eeePC system finds the printer - when I tell it to look at 192.168.1.30 (LAN IP for the printer) it pops up as a "Lexmark 6500 series". But that's about it. Any attempt to print wanders off into never never land.

Any ideas where I might go next? I didn't really follow the CUPS help about LPR/D printers.

Cheers IB

---

### Post by lykwydchykyn on 2009-05-25
Check the cups log in /var/log/cups/error_log.  Sometimes I've noticed that some printers get strange default settings that cause print jobs to fail.  You might want to run down the printer's settings and make sure everything is relatively sane (e.g., it's not trying to pull from a nonexistant tray or use a paper size you don't have).

---

### Post by cmost on 2009-05-25
From my experience, Lexmark printers are not very well supported in Linux.  Please be sure to write Lexmark and inform them of your choice of operating system and demand they provide some support.  It seems as if these companies can provide support for Mac OS-X, it shouldn't be that big a stretch to provide Linux support too, since these two Operating Systems share a common ancestor in UNIX.  That being said, HP and Epson printers are very well supported in Linux.

---

