---
title: "odd cups issue"
date: 2006-02-27
forum: Desktop Environments
---

### Post by ed_d on 2006-02-27
OK, I was able to build a printer a bit back and be able to go into it using the apps>sys>admin>printers. Now, when I try to do this I get a Error message that pos up and says: "The CUPS server could not be contacted." I also did run with and without sudo "gnome-cups-manager" and I get:
** (gnome-cups-manager:7983): WARNING **: IPP request failed with status 1280

** (gnome-cups-manager:7983): WARNING **: IPP request failed with status 1280
 
Anyone had this? Please advise. It happens on my sones PC too, as he is running Ubuntu as well. Just want to get it so that we can all print to it. Now If I wan to change my printer, I cant. BTW its a HP PSC1401 and like I said was working before.

---

### Post by swamytk on 2006-02-28
IPP (Internet Printing Protocol) listen at ip address 127.0.0.1 and port 631 by default (check with "Listen 127.0.0.1:631" line in /etc/cups/cupsd.conf). It seems to be IPP is not able to listen in your case.
1. Ensure that loopback device is running in your system by issuing "ifconfig lo" command. it should list the ip address 127.0.0.1 as interface.
2. If 127.0.0.1 is not running, try running manually like "ifup lo" command.
3. Now try running the Printer wizard in apps>sys>admin>printers.
4. If the problem is solved, check with any latest software you installed. (e.g. ltsp-client software may cause problem). Uninstall/reconfigure this misbehaving application properly. You can identify this odd application by booting ubuntu in recovery mode.

---

