---
title: "How do you add a network printer?"
date: 2005-03-09
forum: Desktop Environments
---

### Post by zcox on 2005-03-09
Hi all - hopefully this is the right forum to post in, if not please let me know a more appropriate one.

I have a HP PhotoSmart 2610 printer connected to my Linksys router (so it's not connected to another computer or print server). I have several Windows machines successfully printing with it over the network. The Ubuntu Add Printer wizard is great for local printers, but I'm having trouble setting up this network printer.

First off, I have no clue whether to use CUPS, Windows Printer, UNIX Printer, or HP JetDirect. And then, I have no clue what parameters to use for each one. Can anyone provide any sort of guidance? [-o<

---

### Post by picturesqueweb on 2005-03-09
I'm having exactly the same issue only with a Tektronics Phaser 850. Ubuntu is great for everything else I've tried to do, but setting up this printer has me totally baffled.

---

### Post by sysrq on 2005-03-09
It will probably be a LPR, Unix Printer, if that doesnt work just take a stab at the other options.

---

### Post by zcox on 2005-03-10
[QUOTE=sysrq]It will probably be a LPR, Unix Printer, if that doesnt work just take a stab at the other options.[/QUOTE]
 I got it working using the "take a stab" approach.  I looked at my router settings and got the IP address of the printer, then in the Add Printer wizard I selected HP JetDirect (not sure if this only works for HP printers?), put in the printer's IP address, left the default Port at 9100 and clicked next.  My HP Photosmart 2610 wasn't in the printers list, so I downloaded the ppd file from linuxprinting.org and specified it.  Then clicked apply and it worked!

---

### Post by picturesqueweb on 2005-03-10
I've stabbed and stabbed. It does seem like setting changes are not saved. I have to delete the printer and then install new. Isn't there any way of scanning the network for supported printers? Others do it. Ubuntu is too great a distro not to have such a feature. Wish I had the know how to create this feature myself.

Anyone out there have more step by step instructs? [-o<

---

### Post by Jack Monaghan on 2005-03-10
You can try editing /etc/cups/cupsd-browsing-conf and change "Browsing Off" to "Browsing On" it is what i had to do to enable network printing but i am running all linux
so i am not sure if it will help.

---

### Post by picturesqueweb on 2005-03-10
The reply above filled in the missing detail. Thank you!!!

Here's what I did...

edited /etc/cups/cupsd.conf changing "Browsing Off" to "Browsing On"
went into Computer/System Configuration/Printing
added a new printer choosing Unix LPD
as host, just entered the IP address for the printer
for queue just enter whatever you want
next and select the printer
test sheet seconds after clicking the test page button

Thank you all for your responses!

---

