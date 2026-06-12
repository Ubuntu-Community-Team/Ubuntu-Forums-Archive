---
title: "Where are the Printer Drivers?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by jakestah7 on 2006-06-07
-On Dapper Drake-

On a dell desktop pc, I was trying to get a Hp officejet 5510 to work. . . When I go to the printer set up and press forward, on the list of models/brands there are none, there is nothing when you click on the down arrow icon. This is very strange; what should I do . . . I would like to try something before I reinstall the whole OS.

P.S.
I first had breezy but, upgraded to dapper and when I wanted to reinstall printer this happend

---

### Post by meng on 2006-06-07
You can download PPD files which are used as printer drivers from [www.linuxprinting.org](www.linuxprinting.org). That is one weird problem you have though.

---

### Post by wpshooter on 2006-06-07
I installed Dapper Drake from scratch (did not upgrade beta or from previous release) and the drivers (I think 5 or 6 of them) for my HP laserjet 2100 were there.  Sounds like something went wrong in your install/upgrade.  I am new to this, so unfortunately, I could not tell you how to fix other than trying to reinstall.

But let me say that I am somewhat disappointed with the handling of printer drivers in Ubuntu/linux.  Of the 5 or 6 listed for my printer only one seems to function correctly.  The one that was listed as recommended did NOT work properly.  When I went searching for printer drivers the only one I could find for my HP was the one that was listed in Ubuntu as recommended and as I said it did not work properly.  I believe that I have also searched for compatible drivers on the HP site and there is none.  I believe Ubuntu/linux needs some more effort into the area of printer driver offerings.

Good luck.

---

### Post by dk_pa on 2006-06-11
I have the same problem plus more!

I haven't been able to get the right driver it seems for my LaserJet4 Plus and I removed it to reinstall it and now I can't do anything!  You see the option of "installing a driver" does nothing for me beacuse it just says the driver is already installed and nothing shows up on the list so I can't finish the install.

I tried the CUPS interface but it keeps rejecting my username and password.  I checked to make sure I was part of the system group it looks for and I am so I'm not really sure here :|

---

### Post by NinjitsuStylee on 2006-06-12
Ok, Update.

I don't know where the drivers are but I managed to get printing to work nevertheless.  I simply installed the hpijs package and it puts drivers in the following directory:

/usr/share/ppd/hpijs

When you're asked to select the printer driver, just click the "install a driver" button and manually locate the file.

I use an HP PSC 1315 (it uses the 1310 driver) and I got mine to work right away, even scanning with xsane!

I did the same thing by the way...upgraded from Breezy 5.10 to Dapper 6.06.  A lot of stuff is broken but other than that dapper's not too bad!

---

### Post by paul cooke on 2006-06-13
[QUOTE=NinjitsuStylee]Ok, Update.

I don't know where the drivers are but I managed to get printing to work nevertheless.  I simply installed the hpijs package and it puts drivers in the following directory:

/usr/share/ppd/hpijs

When you're asked to select the printer driver, just click the "install a driver" button and manually locate the file.

I use an HP PSC 1315 (it uses the 1310 driver) and I got mine to work right away, even scanning with xsane!

I did the same thing by the way...upgraded from Breezy 5.10 to Dapper 6.06.  A lot of stuff is broken but other than that dapper's not too bad![/QUOTE]

so why doesn't the KDE add printer wizard look in there then? all it gives me for it's database is a paltry list of 4 HP printers... and it's NOT obvious that the others are available as unless you specifically know that you need hpijs, then you haven't a scooby like the vast majority of our users.

The annoying thing is that the printer name and model was available to the wizard when you selected it from the list of detected items... the wizard really needs some more intelligence coding in to make things idiot proof... It was only your post that gave me the location to search in. :-(

---

