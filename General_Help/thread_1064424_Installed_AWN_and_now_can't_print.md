---
title: "Installed AWN and now can't print"
date: 2009-02-08
forum: General Help
---

### Post by twowheeler on 2009-02-08
I have installed AWN on Hardy and it works well except that suddenly I have problems printing.  Some apps seem to have their own print setup and they work fine, like openoffice and gimp.  Also this hardy machine is the print server for a network of other PCs, and they have no problems printing.  However other gnome apps just hang when the print item from the menu is selected, until I have to kill the app to get it off the screen.  For example eog, firefox, gedit, etc.  In firefox, it will hang even if I just open the Page Setup box and try to select a printer.  

The printer is a Epson CX5200, and the drivers are from foomatic and gutenprint.  I reinstalled both of those but no change.

Before AWN this machine was solid as can be.  I am ready to dump AWN but thought I would see if there is a fix in the forums first.

Anyone?

---

### Post by Kobalt on 2009-02-09
How did you install AWN? Is it an experimental version or a stable one? If you used a package or repository, there may have been a dependency problem that removed some packages...

---

### Post by johnjohn2 on 2009-02-09
Hey

Never heard anything like that before, but as the previous post saidare you using the stable experimental version

---

### Post by twowheeler on 2009-02-09
I installed it from the repo at:
[http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu)
It shows a version like 0.3.1bzr939.1~hardy

BTW I checked out CUPS at 127.0.0.1:631, and it looks like it is running normally.  When the problem occurs, a job never appears in the CUPS system.  It is dying in gnome before handing off to CUPS.

---

### Post by twowheeler on 2009-02-09
Well, I did a full uninstall of AWN, and the problem persisted.  So something has been clobbered in gnome by AWN and I don't know how to track it down.  Still looking for help and suggestions.  I need my printer back.

Edit:  Sorry, it had nothing to do with AWN.  I screwed up the /etc/hosts file, so the system was searching for a nonexistent IP.  Fixed now.

---

