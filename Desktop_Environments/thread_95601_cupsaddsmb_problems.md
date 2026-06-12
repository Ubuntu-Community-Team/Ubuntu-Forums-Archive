---
title: "cupsaddsmb problems"
date: 2005-11-26
forum: Desktop Environments
---

### Post by pmshoop on 2005-11-26
Hey all, 
Problem with cupsaddsmb I need help with.  I run the command and it keeps hanging at the password for accessing server via SAMBA.  Here's the output from running -v option

sudo cupsaddsmb -H brainiac -v OfficeJet-T45
Password for root required to access brainiac via SAMBA:
Running command: smbclient //brainiac/print\$ -N -U'root%secret' -c 'mkdir W32X86;put /var/spool/cups/tmp/43892a5b8dffa W32X86/OfficeJet-T45.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Error connecting to 127.0.0.1 (Connection refused)
Connection to brainiac failed


so, any ideas?????? need help BIG TIME

---

### Post by pmshoop on 2005-11-27
Bump

---

