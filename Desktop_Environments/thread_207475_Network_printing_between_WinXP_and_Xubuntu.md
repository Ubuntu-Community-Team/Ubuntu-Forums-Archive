---
title: "Network printing between WinXP and Xubuntu"
date: 2006-07-01
forum: Desktop Environments
---

### Post by rlgoddard on 2006-07-01
Hi,

I am having trouble adding a printer in WinXP.  I've already setup samba in Xubuntu by apt-get samba and smbfs.  In Windows, whenever I tried to add the printer attached to the comptuer running Xubuntu, I get a password and username prompt.  I can't get past it.

After setting up the password and username, is there anything else I need to be doing to enable printing from WinXP to Xubuntu?  Thanks in advance for your help!

Take care,
Russ

PS:  I don't have any Gnome or KDE apps -- I'm running pure XFCE :)

---

### Post by WW on 2006-07-01
You shouldn't need samba to share a printer--CUPS can handle it.  Take a look here:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by rlgoddard on 2006-07-02
Hi,

Looks like after I modified the cups.conf file, this happened:

cupsd:  Child exited with status 1!

This was after I restarted the cupsd server.  I can no longer access [http://localhost:631]("http://localhost:631").

Take care,
Russ

Edit:  Looks like I renames the conf file wrong.  I changed it to cupsd.conf, and it works.  However, I'm still unable to connect to the printer using the link you sent me.  Windows complains about not finding the printer.

---

