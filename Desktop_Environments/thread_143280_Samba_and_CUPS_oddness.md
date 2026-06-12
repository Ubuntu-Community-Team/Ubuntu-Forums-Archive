---
title: "Samba and CUPS oddness"
date: 2006-03-12
forum: Desktop Environments
---

### Post by Blairboy on 2006-03-12
ok, I *think* I have samba and cups setup decently correct.  I installed gutenprint the other day and very happily printed a test page to an Epson Stylus Photo R800 connected to a windows machine on my network (Giant).  I tried actually printing to it yesterday and no dice.  So, I read as much as I could  about the situation and came up modifying two config files: smb.conf and printers.conf.

My printers.conf reads as follows:

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sat 11 Mar 2006 10:58:14 PM CST
<Printer DeskJet-722C>
Info DeskJet-722C
DeviceURI smb://GUEST@GIANT/722C
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
<DefaultPrinter LaserJet-6L>
Info LaserJet-6L
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
<Printer Stylus-Photo-R800---CUPS+Gutenprint-v5.0.0-rc2>
Info Stylus-Photo-R800---CUPS+Gutenprint-v5.0.0-rc2
DeviceURI smb://GUEST@GIANT/R800
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>




And my smb.conf reads like this:

[global]
   workgroup = HOME
   netbios name = Deus
   server string = Deus
   security = share
   dns proxy = no
   log file = /var/log/samba/log.%m
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   load printers = yes
   printing = cups
   printcap name = cups
   printer admin = root
   socket options = TCP_NODELAY

[homes]
   comment = Home Directories
   browseable = no

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = no

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    browseable = yes
    read only = yes
    guest ok = yes



Now, the really odd part is that I have two winxp machines on this network, but the one with the printers I want to use doesn't list in network:///.  However, I can manually connect to it with smb://Giant.  Also, when I launch network, the other computer keeps saying that authentication is required and asks me for user name, domain, and password.  Which, it doesn't accept anything.  Even if I use Guest, or my actual winxp login info, I get nothing and the Authentication Required window keeps coming up until I hit cancel.  I still can't print to the xp machine with the networked printers.  Can anybody help me?

---

