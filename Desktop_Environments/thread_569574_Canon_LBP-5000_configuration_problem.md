---
title: "Canon LBP-5000 configuration problem"
date: 2007-10-07
forum: Desktop Environments
---

### Post by dannesthlm on 2007-10-07
Hi

Accrding to the following instructions in [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900), i'm trying to make a canon LBP-5000 to work on ubuntu32/7.10. 

There are absolute no problems in the process worth mention, even the last check (captstatusui -P LBP5000) givs the correct information, it says the printer i buysy when it's warming up and "ready to print" when it's not.

The problem: When i'm trying to print (whatever) nothing happens. The document goes from "processing" to "held". The printer works in Windows, so it's not hardware related.

Regards,

Daniel

---

### Post by pmorton on 2007-12-08
> **dannesthlm said:**
> Hi
Accrding to the following instructions in [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900), i'm trying to make a canon LBP-5000 to work on ubuntu32/7.10. 
The problem: When i'm trying to print (whatever) nothing happens. The document goes from "processing" to "held". The printer works in Windows, so it's not hardware related.
Regards,
Daniel

I've had  exactly the same problem with the LBP-5000 and 7.10. The answer was here:

[http://ubuntuforums.org/showthread.php?t=134937&highlight=lbp5000&page=2](http://ubuntuforums.org/showthread.php?t=134937&highlight=lbp5000&page=2)

in a post by Jellus. For some odd reason there's an updated 1.5 driver that works only on Canon's Australia web site. 

The dummy lib to which Jellus links is needed for Gutsy, and the command:

$ sudo /usr/sbin/ccpdadmin -p [printer model as you want it named] -o /dev/usblp0

as far as I can make out,  should read:

$ sudo /usr/sbin/ccpdadmin -p [printer model as you want it named] -o /dev/usb/lp0


Canon's GNU/Linux support might be scatty, but my Canon LBP5000 now works!!

---

