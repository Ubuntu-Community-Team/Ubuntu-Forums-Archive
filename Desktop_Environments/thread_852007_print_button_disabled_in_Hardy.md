---
title: "print button disabled in Hardy"
date: 2008-07-07
forum: Desktop Environments
---

### Post by misja on 2008-07-07
I have upgraded my pc from Gutsy to Hardy, and now when I press 'print' to print something, the print dialog that comes up that lets me select a printer has my 'print' button disabled.
In Gutsy everything still worked fine; also when I go to administration-Printing and I print a test page it comes out fine. In Opera I can still print as well.
The applications that have the 'print' button disabled in the print dialog are for instance Gedit, Document viewer (for pdf's) and Firefox. Basicly everything that uses the standard Gnome print dialog.

Does anybody know how I could fix this?

---

### Post by VMC on 2008-07-07
Maybe your printer is not setup. Go to "System > Administration > Printing" and check the status.

Edit. okay, the how about the Device URI? Is it correct?

---

### Post by misja on 2008-07-08
Yeah the device URI is correct. It still was working last week before I upgraded and I haven't changed it.
Also I have just copied a printer configuration from a colleague who is also using Hardy (and doesn't have my problem), but on my pc again the Print button is disabled ...

---

### Post by misja on 2008-07-09
So nobody knows? Does anybody know where I should look (which logfiles and where) so that I could perhaps solve this problem by myself?

---

### Post by lunatico on 2008-08-27
Having the same issue here. From Firefox it is always disabled. My work around is to print to a pdf file and then print the pdf with evience. But with evience the same issue sometimes happen. Very confusing...
Anyone?

---

### Post by jonas.eberle on 2009-03-31
=========================================== 
I had the same problem in Hardy.
Only the GTK-print dialog is affected, I can print fine from KDE-programs.

system-config-printer shows the printer, test page works fine.

The machine is setup to print via CUPS. Printer is a HP LaserJet 2100. It is connected via Parallel Port, the URI is hp:/par/HP_LaserJet_2100_Series?device=/dev/parport0.

============================================

I edited /etc/cups/cupsd.conf:

in <policy default>
for SEND-DOCUMENT
edit "user @OWNER @SYSTEM" to "user"

then ```
sudo /etc/init.d/cupsys restart
```

Worked for me so far.

---

