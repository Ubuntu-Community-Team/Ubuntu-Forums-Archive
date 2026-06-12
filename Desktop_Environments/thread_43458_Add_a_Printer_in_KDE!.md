---
title: "Add a Printer in KDE?!?"
date: 2005-06-22
forum: Desktop Environments
---

### Post by orev on 2005-06-22
I would like to add a printer to my Kubuntu system, but the information I am finding on installing printers all seems to pertain to Gnome.

Can someone please point me to a url or give me advice on installing a printer in KDE?

Specifically, I am trying to use a Canon i860.

Your kindness will be repaid... :)

---

### Post by Yeldarb on 2005-06-22
[QUOTE=orev]I would like to add a printer to my Kubuntu system, but the information I am finding on installing printers all seems to pertain to Gnome.

Can someone please point me to a url or give me advice on installing a printer in KDE?

Specifically, I am trying to use a Canon i860.

Your kindness will be repaid... :)[/QUOTE]
 If you go to the *Control Center* (In the *K Menu*), under *Peripherals*, there should be a *Printers* section.  Click add in the top right corner, select *Add* | *Add Printer/Class* and go through the wizard.  Then you should be all set.

---

### Post by orev on 2005-06-22
I would like to do this, but the add>add printer/class is not selectable for me.  Maybe something to do with permissions of some sort?!?

Please advise...

THANK YOU!

---

### Post by orev on 2005-06-22
After restarting system and installing cups I was able to use this "how to":

[http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860](http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860)

Thanks!

---

### Post by Zeddicus on 2005-06-22
[QUOTE=orev]I would like to do this, but the add>add printer/class is not selectable for me.  Maybe something to do with permissions of some sort?!?
[/QUOTE]

I'm guessing I know what your problem is -- it's one I've dealt with myself.

In the printer config screen, look at the bottom right corner for a selection box for "Print System Currently Used:" -- change it from "Generic Unix LPD System" to "CUPS".

Really, this is just poor UI, imo -- even very experienced users can easily miss that. :-/

---

### Post by orev on 2005-06-22
Yeah.  I had some problems switching to CUPS there becuase of some problem with CUPS.  I rebooted my system, then reinstalled CUPS, and then had no problems.

Thanks.... :)

---

