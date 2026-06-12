---
title: "gui installer for pl files ?"
date: 2011-10-14
forum: Desktop Environments
---

### Post by imageblur on 2011-10-14
Is there an add on that has a gui for installing programs?  Installing programs in Windows is all gui driven and easy for our end users.  Is there anything like that for Ubuntu ?

---

### Post by oldos2er on 2011-10-14
Ubuntu Software Center is what you're looking for, but it won't help you with *.pl (Perl?) files.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by imageblur on 2011-10-14
say for instance vmware tools:

sudo ./vmware-install.pl


instead of using the terminal, is there a way that they could just double click the file and a gui would walk them through it ?

---

### Post by mcduck on 2011-10-14
> **imageblur said:**
> say for instance vmware tools:

sudo ./vmware-install.pl


instead of using the terminal, is there a way that they could just double click the file and a gui would walk them through it ?

Yes, the maker of the software could package it properly into a .deb package, installable through the package management. ;)

Just like in Windows where you'll need to package the software into an .exe installer to get it installed through graphical dialogs.

---

### Post by imageblur on 2011-10-14
humm, maybe i'll look to see if i can make my own deb files

---

