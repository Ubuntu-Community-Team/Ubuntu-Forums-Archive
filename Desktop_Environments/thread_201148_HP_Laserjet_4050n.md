---
title: "HP Laserjet 4050n"
date: 2006-06-21
forum: Desktop Environments
---

### Post by chajuram on 2006-06-21
Hi,

I have set up my computer (6.06) to print to a HP Laserjet 4050n printer. I used the recommended postscript printer. When I print a test page from the Printers page, it prints perfectly. But when I print from another application, the page size is miscommunicated. The printer complains of an "Unexpected page size", and hence waits for the manual tray. I have tried to change the page size to various options and have wasted a lot of paper, but invariably, the page size is wrong and part of the document is not printed on paper (lower part cut-off).

Linuxprinting.org says the printer HP laserjet 4050 (without the 'n') works perfectly, so I am hopeful.

Any suggestions will be very welcome.

Chajuram.

---

### Post by Michaeldaley on 2006-07-05
I had the same problem with my 4050t, and this is how I fixed it:

You need to remove the printer that you have installed and re-install it using the cups installation found here: [http://localhost:631/admin](http://localhost:631/admin)

The only problem is that cups doesn't work in Dapper, but I found a fix for that here:
[http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/](http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/)

Now, your printer is pulling from the wrong tray because of a bogus driver.  When installing in cups, choose this driver instead: hp laserjet 4050 foomatic/hpijs - HPLIP 0.9.7 (en) 

and then make sure to specify the paper type and leave the tray set to default.

This would probably work for any similar hp laserjet probs, just choose the foomatic/hpijs driver instead of the recommended postscript one.

---

### Post by chajuram on 2006-07-09
Wow Michaeldaley, I had lost all hope. I will try your solution tomorrow.

---

### Post by Michaeldaley on 2006-11-13
UPDATE! I managed to login to cups without messing with the user lists since Edgy has been released.

---

### Post by tc7 on 2008-02-13
I found the HP postscript (recommended) driver worked fine with the test page, but would result in a document error 1-2 minutes after trying to print. I tried various settings but could not get a single document to print.

Using the following alternate driver fixed the problem: HP LaserJet 4050 - CUPS+Gutenprint v5.0.1
I haven't tried the foomatic drivers. 

I'm using system-config-printer (rather than gnome printer config) - seems to be more comprehensive.

---

