---
title: "samba printing setup setback"
date: 2006-02-09
forum: Desktop Environments
---

### Post by rudeboyskunk on 2006-02-09
Ok, so I've gotten through most of the samba print server setup.  However, when I try to do "cupsaddsmb -a", this is what I get:

root@ashbysucks:/home/rudeboyskunk# cupsaddsmb -a
Password for root required to access localhost via SAMBA:
Password for root required to access localhost via SAMBA:
Password for root required to access localhost via SAMBA:


It does this if I'm root or not root.  It just keeps asking for my password, and I keep entering it.

---

### Post by olafura on 2006-02-09
Try installing selinux-utils and doing:
sudo setsebool smbd_disable_trans 1
sudo /etc/init.d/samba restart

This is a problem with selinux blocking samba


Olafur Arason

---

### Post by rudeboyskunk on 2006-02-09
[QUOTE=olafura]Try installing selinux-utils and doing:
sudo setsebool smbd_disable_trans 1
sudo /etc/init.d/samba restart

This is a problem with selinux blocking samba


Olafur Arason[/QUOTE]


ok i tried that, didn't work.  however, i used verbose mode and came up with this:

root@ashbysucks:/home/rudeboyskunk# cupsaddsmb -a -v
Password for root required to access localhost via SAMBA:
Running command: rpcclient localhost -N -U'root%*mypassword*' -c 'setdriver DeskJet-920C DeskJet-920C'
failed session setup with NT_STATUS_LOGON_FAILURE
Cannot connect to server.  Error was NT_STATUS_LOGON_FAILURE

Password for root required to access localhost via SAMBA:




I also tried this as not root.  Didn't work, but looked like this:

rudeboyskunk@ashbysucks:~$ cupsaddsmb -a -v
Password for rudeboyskunk required to access localhost via SAMBA:
Running command: rpcclient localhost -N -U'rudeboyskunk%*mypassword*' -c 'setdriver DeskJet-920C DeskJet-920C'
SetPrinter call failed!
result was WERR_ACCESS_DENIED

Password for rudeboyskunk required to access localhost via SAMBA:

---

### Post by olafura on 2006-02-10
Then it's just a bug that has to fixed. 
selinux-utils didn't have setsebool in dapper so I could test it.
I can file a bug for it if you want to, otherwise this page has
information about this:
[http://forums.fedoraforum.org/showthread.php?p=365558#post365558](http://forums.fedoraforum.org/showthread.php?p=365558#post365558)

Olafur Arason

---

### Post by olafura on 2006-02-10
Sorry I spoke to soon.
set 
use client driver = No
in [printers] in /etc/samba/smb.conf

Olafur Arason

---

