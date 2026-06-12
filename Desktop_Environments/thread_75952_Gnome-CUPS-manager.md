---
title: "Gnome-CUPS-manager"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Hellbourne on 2005-10-14
Hi everyone,

I recently installed Ubuntu 5.10 on my computer (three days ago) and everything seems to be operating normally except for my printer.

I have an HP Officejet 5510, which ptal-setup detected correctly and started the HP Linux driver successfully for it.

However, when I click on System/Administration/Printing in my Gnome, nothing happens, that is to say the gnome-cups-manager loads in the system monitor, but other than that, nothing happens. Moreover, after about 5 (!) minutes, I get an error message saying that "the CUPS server could no be contacted".

Does anyone know what the illness and its cure are?

If it helps, I get this long delay also when I click on System/Admin/Disks or Network, but in those cases they work. In addition, the Sane program manages to communicate with the scanner

Many thanks,

Amit.

---

### Post by 11hjpphty76lkjj on 2005-10-17
How about try restarting CUPS and HPLIP?

terminal
sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart

And try it again..

If not do a
terminal
tail -f /var/log/messages

and copy and paste any errors you see.

Also try running hp-info and send me what it says in there as well.

Aaron

---

### Post by sinbad782 on 2005-10-19
Hi, The problem I have with this is that when you open the System -> Administration -> Printing app (gnome-cups-manager), and click on 'Add Printer' the app crashes after the add printer dialogue pops up. 

I have reported this to the developers using the bug buddy tool.

---

### Post by redson on 2005-10-19
I just encountered a similar problem, though I didn't let it run long enough to see if the error message pop-up.

the issue turned out to be I'd edited my /etc/cups/client.conf and changed my ServerName to an invalid value

Specifically I'd set ServerName to the wrong IP address (typo).

---

