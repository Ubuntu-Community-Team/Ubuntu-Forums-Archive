---
title: "Printer nearly works! HL-1430"
date: 2006-07-24
forum: Desktop Environments
---

### Post by WhoDaBear on 2006-07-24
Hi folks.

Thanks for help from "Da Community" so far.

Here's another problem I've been unable to sort out.  Hopefully someone will take pitty on the newbie!

Printing
I appear to be allowed only one print (which is very slow) per boot!  After the magic print emegrges from my Brother HL-1430, no other documents will print at all until I reboot.  The printer icon remains in the system tray, but will admit to having no jobs!  System -> Printers   will reveal that correct number of jobs in the que, but just claims they are printing.

Thanks in advance.

WhoDaBear

---

### Post by pkolloch on 2006-08-25
Hi,

I have the same problem as well. It is discussed in

[http://www.ubuntuforums.org/showthread.php?t=240549](http://www.ubuntuforums.org/showthread.php?t=240549)

too. I do not have to reboot though. It is sufficient to switch the printer off and on again (allow a second or so in between) and then stop and start the printer in CUPS. This is majorly annoying, so if anyone has a fix...

CUPS reports the following status:


printer-state-message
Printer not connected; will retry in 30 seconds...
printer-state-reasons
connecting-to-device

(BTW, another workaround seems to be to use a traditional printer cable connected to the parallel port)

---

