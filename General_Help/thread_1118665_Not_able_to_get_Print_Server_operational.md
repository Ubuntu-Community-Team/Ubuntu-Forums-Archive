---
title: "Not able to get Print Server operational"
date: 2009-04-07
forum: General Help
---

### Post by zoomiest on 2009-04-07
This is my first time setting up Samba to be the house print server.

[LIST]I just got the shares working with SAMBA.[/LIST]
[LIST]I have installed cups. (but didn't modify the .conf file)[/LIST]
[LIST]I have the printer blugged into the samba box.[/LIST]
My smb.conf printer settings are as follows:


```

####Printing#####
load printers = yes
printing = cups
printcap name = cups

[printers]
   comment = All Printers
   browseable = yes
#  path = /var/spool/samba
   path = /tmp
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   create mode = 0700
   use client driver = yes


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   read only = yes
   browseable = yes
#  path = /var/spool/samba
   path = /tmp
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   create mode = 0700
   use client driver = yes
   guest ok = yes


```

And, yes, I restart Samba, after smb.conf mods.

From here, I just go to my WinXP machine, and try to add a printer. I can see the two Samba servers, but no printers show themselves to select...

Is that right?
Do I have to specify a printer at the server level?
(Its a Samsung ML-4500)

---

