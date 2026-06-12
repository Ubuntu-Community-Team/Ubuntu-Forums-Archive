---
title: "pushing windows drivers with samba"
date: 2009-04-04
forum: General Help
---

### Post by BarryDocks on 2009-04-04
I am trying to set up a print server with ubuntu server edition 8.04 with the windows printer driver automatically 'pushed' to the windows clients, but I get the following error each time I run cupsaddsmb command:

Unable to copy Windows 2000 printer driver files (1)!
Running command: smbclient //localhost/print$ -N -A /var/spool/cups/tmp/44cb9359ab2bb -c 'mkdir W32X86;put /var/spool/cups/tmp/44cb9354030f8 W32X86/HPofficejet.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Domain=[FPIG] OS=[Unix] Server=[Samba 3.0.22]
NT_STATUS_NETWORK_ACCESS_DENIED making remote directory \W32X86

I have tried the following suggestions:
[http://ubuntuforums.org/archive/index.php/t-225425.html](http://ubuntuforums.org/archive/index.php/t-225425.html)

[http://wdhawes.blogspot.com/2007/03/sharing-printers-with-windows-clients.html](http://wdhawes.blogspot.com/2007/03/sharing-printers-with-windows-clients.html)

[http://www.issociate.de/board/post/284929/SAMBA_Privileges_using_cupsaddsmb.html](http://www.issociate.de/board/post/284929/SAMBA_Privileges_using_cupsaddsmb.html)

I've even tried manual 15 step installation which fails at the rcclient command
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html)

Has anyone got a definative answer to this problem?  If so could detailed instructions please be posted?

Struggled for over a week with this one ](*,)
Thanks

---

