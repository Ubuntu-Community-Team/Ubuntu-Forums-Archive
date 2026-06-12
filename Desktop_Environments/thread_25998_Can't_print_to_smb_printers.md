---
title: "Can't print to smb printers"
date: 2005-04-11
forum: Desktop Environments
---

### Post by djjazzy on 2005-04-11
Hi all, just installed hoary generel release on Friday, best Linux install I've ever experienced! I'm a sysadmin that has used a few distros since swearing off winblows last year, have all my tools together with hoary except I can't get printing to 2k print server based printers. Am in 2003 domain, I have created machine account for my Ubuntu box and am having strange results with Printer applet in Gnome but have been unable to get anything out of the printer. Is this a hoary issue and can anyone help out a Linux noob that doesn't want to use m$ products ever again, thanks..........Jeff

---

### Post by orion_114 on 2005-04-11
Check this thread .....
[http://ubuntuforums.org/showthread.php?p=124137#post124137](http://ubuntuforums.org/showthread.php?p=124137#post124137)
It might help u out.

---

### Post by djjazzy on 2005-04-11
Thanks for the reply Orion, didn't help tho. I saw this thread earlier but it didn't mention how to specify the 2003 domain. The account I use to access this smb printer is my domain account, I have no account on the print server machine itself. I've set this device uri in /etc/cups/printers.conf:

smb://domain/woodman:mypassword@10.10.0.76/deforest

where deforest is the printer sharename. With this setting in printers.conf, when I setup a printer through gnome-cups and specify host, share, user and password, then apply, I get no printout. Also the above values are replaced when I go back into gnome-cups with the domain in the host slot and the above uri in the share slot. Ouch!

---

### Post by orion_114 on 2005-04-11
Sorry I coldn't be of any more help djjazzy.
I unfortunatly dont have a Win2003 Domain to test to help u out.
Sorry. :(

---

### Post by djjazzy on 2005-04-11
No problem Orion, thanks for taking the time, I'll get it sooner or later. :???:

---

### Post by orion_114 on 2005-04-11
Try the official samba documentation ..
[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

