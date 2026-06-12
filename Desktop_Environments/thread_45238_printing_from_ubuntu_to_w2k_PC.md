---
title: "printing from ubuntu to w2k PC"
date: 2005-06-29
forum: Desktop Environments
---

### Post by GOwin on 2005-06-29
Our network are mostly Windows machines except for mine, which Ubuntu HH 

One of the Windows computer has an HP LaserJet 1100 printer. I can see the
computer with the printer just fine (I can browse through it's shared folder, etc), but when it comes to printing through the printer attached to it, I have some problems.  

The following are the results of "smbclient -L pc1 -U administrator " from the terminal:


Domain=[WORKNET] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

Sharename Type Comment
--------- ---- -------
HPPS735 (E) Disk
Bkp_Pictures Disk
IPC$ IPC Remote IPC
D$ Disk Default share
print$ Disk Printer Drivers
SharedDocs Disk
G$ Disk Default share
Printer5 Printer Acrobat Distiller
ADMIN$ Disk Remote Admin
C$ Disk Default share
lj1100 Printer attached to desktop

Domain=[WORKNET] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

Server Comment
--------- -------

Workgroup Master
--------- -------
-------------------------------------------------------------------------- 

I tried 'lpadmin -p Laserjet1100  -v smb://administrator:password@pc1/lj100 P
/root/inkjet.ppd' but i got the following error:
'lpadmin: add-printer (set model) failed: client-error-not-found'

If I then go into the gnome-cups-manager the new printer shows up but does not work. When I try to print a test page, I get :

'Printing to 'laserjet1100' failed with error code: 1286
is the printer paused ?' 

Nope, the printer isn't paused.

Help please.

---

### Post by GOwin on 2005-06-29
*bump*

anyone?

---

