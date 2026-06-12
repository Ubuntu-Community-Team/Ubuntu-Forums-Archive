---
title: "can't add printer in gnome...please help"
date: 2006-08-23
forum: Desktop Environments
---

### Post by harty83 on 2006-08-23
I open gnome-cups-manager and try to install a printer but no printer drivers are showing up; no manufacturers, no models, no drivers.  They show up in the cups web interface and under kde but they do not show up under gnome.

Any suggestions?

---

### Post by harty83 on 2006-08-23
This was in my error log:

E [20/Aug/2006:10:40:00 -0400] Creating missing directory "/var/run/cups/certs"
E [23/Aug/2006:22:32:49 -0400] Creating missing directory "/var/run/cups/certs"
E [23/Aug/2006:22:49:35 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Aug/2006:22:49:44 -0400] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [23/Aug/2006:22:49:44 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Aug/2006:22:55:56 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Aug/2006:23:06:41 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Aug/2006:23:06:49 -0400] CUPS-Add-Modify-Printer: Unauthorized


is it related?

---

### Post by harty83 on 2006-08-28
I still can't find a way to install printers under gnome.  I've tried to install it under kde and in cupsys web admin but gnome still doesn't recongnize the printer.  It still does give me a list of drivers to install.

I've tried to completely remove (purge) all cupsys everything (except libcupsys) and gnome-cups-manager and reinstalled but it didn't work.

Please help!!  I'm completely rendered printerless.  ANY suggestions will be greatly appreciated!!!

---

### Post by mbeierl on 2006-08-31
Well, I've got no help.  I happen to be in the exact same boat - gnome-cups-manager shows no printer manufacturers/drivers.  I browse for a .ppd file to install, find the one for my printer, and add it - only to have cups tell me it's already installed!

Help either of us, please? :)

---

### Post by promet on 2006-09-01
I had this problem also and uninstalling and reinstalling gnome-cups-manager from within Synaptic worked well for me. Hope this is of some help.

---

### Post by harty83 on 2006-09-01
I have already tried that with purging gnome-cups-manager and resintalling it and it still did not work.

---

