---
title: "help - no permission to print"
date: 2009-01-12
forum: General Help
---

### Post by Wolf-Ekkehard on 2009-01-12
After the KDE4 "printing" utility forced me to reinstall my printers (Brother HL-5250DN on a parallel port and Canon BJC-3000 on a USB port) I get a "permission denied" error from the CUPS WEB interface when I try to print (test page or otherwise).  I checked that /dev/lp0 and /dev/usb/lp0 are both owned by user "root" and group "lp" and have r/w permission for both:  
```

$ ls -l /dev/lp0 /dev/usb/lp0
crw-rw---- 1 root lp   6, 0 2009-01-10 16:20 /dev/lp0
crw-rw---- 1 root lp 180, 0 2009-01-10 16:20 /dev/usb/lp0

```
I also checked that I am in group lp (and lpadmin) - but still I get "permission denied" .  When I add
```
sudo chmod o+rw /dev/lp0
```
I can print (until the next reboot when this extended permission nonsense gets cleaned up again), but this ain't right - I should have permission to read/write that device if I am in the lp group - right?

What am I doing wrong???  Anybody out there who knows what is haunting my print system, or me?

---

### Post by Wolf-Ekkehard on 2009-01-24
I guess nobody wants to take on this one :(

I figured out that "I" am allowed to access the printers, but "something" which tries to print my print jobs is not (cupsd??).  Who owns these processes and why would the owner of a print process not be member of lp????

Also, very weird things happen: When other machines are on the LAN that used to print via mine, I can see their remote print queues in the list of printers whenever I hit the print button on any application.  Additionally, the ability to print on both sides of the paper with my Brother is gone, even though I can still select the option - just doesn't do it.  Moreover, it always wants to add my Canon printer with its own queue name, ignoring mine.  Printing to pdf files doesn't always work anymore either...

In short, CUPS is hosed.

How do I "re-install" CUPS?  When I take it off, does it leave config files behind that need to be cleaned up by hand?  Can I just get generic config files from some place instead of going through the re-install process?  What is the best plan of attack? Anybody done this before?

---

### Post by Wolf-Ekkehard on 2009-01-25
After I wasted the better part of an otherwise perfectly good Saturday afternoon on this, I can answer all of the questions above myself.

When I looked at my /etc/cupsd.conf, I discovered that KDE4's system-config-printer-kde messed that one up beyond recognition - really!!  I got a saved copy of that file back and things started to improve.  1) The issue with permissions is solved by having a line "Group lp" in this file.  If this is missing, cupsd is not allowed to print on a device that belongs to group lp.  2) Stating the correct print queue for my printers magically made the remote print queues disappear from the standard print menu.  3) CUPS offers a foomatic driver for my Brother printer and calls it the "recommended" driver.  Choosing the other and consequentially "not recommended" driver when installing that printer fixed the missing double sided printing option problem.  Turns out the "other" driver was the original Brother driver - maybe CUPS should recommend original drivers and not the foomatic ones?. 4) Adding a virtual pdf printer was straightforward once the cupsd.conf file was fixed.  So there was no need to re-install CUPS, just the /etc/cupsd.conf file.

KDE3 had such a nice "printers" tool in the System Settings with two orders of magnitude more features and considerably less bugs than system-config-printer-kde.py of KDE4; I really miss it as it never let me down.  Then again, given that system-config-printer-kde.py has 36 instances of "FIXME" comments in the code, maybe I shouldn't be too surprised...  I really wish Intrepid would have spared me this KDE4 experience - not just because of the printers tool!

---

