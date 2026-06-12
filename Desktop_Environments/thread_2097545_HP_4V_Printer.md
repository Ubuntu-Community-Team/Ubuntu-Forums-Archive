---
title: "HP 4V Printer"
date: 2012-12-23
forum: Desktop Environments
---

### Post by jsland on 2012-12-23
HP 4V has been used for 11x17 copies since Gutsy without many issues.

Moving from Lucid to 12.04, the printer now spits out 4 essentially blank pages before printing a requested page.

There are 4 lines of "PJL SET ..." at the top of each blank page.  After booting up you can generally get 1 or 2 pages to print correctly before the printer turns into a recyclable garbage generator.

Current driver version is HP LaserJet 4V Foomatic/ljet4 but vitually all have been tried including hplip 3.12.11 installed from shell.

Where is this bug coming from.

---

### Post by jsland on 2012-12-30
Bug was solved by blacklisting kernel module usblp

Thanks to Till Kamppeter at bugs.launchpad.net

---

