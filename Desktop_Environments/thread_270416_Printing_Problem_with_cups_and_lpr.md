---
title: "Printing Problem with cups and lpr"
date: 2006-10-03
forum: Desktop Environments
---

### Post by razahel on 2006-10-03
Hi,

I have a standard install of Dapper 6.06 and I am unable to print to a lpd over the network. 
When i try to send a job then "Spooling lpr job, 2% completed..." appears and nothing changes?

I have a HP Laserjet 4050 on some printserver available and other machines can print to it with the same ppd i have chosen.

Maybe somebody has a hint what to look for.

thanks so far razahel

---

### Post by razahel on 2006-10-03
Has no one an answer or an idea?

---

### Post by bristleburger on 2006-10-03
Does the printer that you are trying to spool to show up in system->administration->printing?

If not you will have to check "detect LAN printers" in Global Settings.

You may also need to execute these commands on the cups server (assuming it's a dapper machine):
root@starbug:/etc/cups# /usr/share/cups/enable_browsing 1
root@starbug:/etc/cups# /usr/share/cups/enable_sharing 1

Once you can see the remote cups server from the host you are printing from, you may need to copy the pdd file from the server to the slave(s). This fixed a number of issues for me:
steve@holly:/etc/cups/ppd$ sudo scp [email]steve@starbug:/etc/cups/ppd/Color-LaserJet-2500.ppd[/email] .
steve@holly:/etc/cups/ppd$ sudo chown cupsys:lp Color-LaserJet-2500.ppd
steve@holly:/etc/cups/ppd$ /etc/init.d/cupsys restart

Goog luck!

---

### Post by razahel on 2006-10-04
Nope sorry does not help.
The printer is added and visible. 
It is no Cups Server I am connecting to it is a real printserver.
If i try to print it always gives me "Spooling lpr job, ...% complete"
but never finishes.

---

### Post by bristleburger on 2006-10-04
Ah, sorry razahel, I don't have any experience of using LAN printers so i don't think I will be able to help.

Presumably you have configured the HP Laserjet 4050 as a Unix printer LPD in cups?

---

### Post by dca on 2006-10-04
Is the printserver its connected to something like a HP JetDirect or is it an honest to goodness print manager or something thereabouts?
 
Instead of using PPD driver, switch to HP Laserjet 4 driver that comes with Ubuntu because I believe that's a generic driver that can at least get test pages printed...

---

### Post by razahel on 2006-10-05
It's a novell netware printserver with free lpd access for some machines without novell.
Here is someone who has nearly the same machine running like mine but startet with the testing version of dapper and he can print.
We find no differences in our installs, but we might have missed some things.

---

### Post by minicruiser on 2007-02-03
cupsdoprint -P cups_printers_name file

---

