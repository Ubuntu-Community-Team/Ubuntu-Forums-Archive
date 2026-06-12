---
title: "Printing to HP C5280 via SAMBA"
date: 2009-01-21
forum: General Help
---

### Post by weetel on 2009-01-21
Hi,

I have successfully installed an HP C5280 on my server version of Ubuntu 8.04 (Hardy Heron) using HPLIP and CUPS.  I can print standard A4 documents both from the command line on the server and via SAMBA from a Windows PC using the official HP Windows driver.

The problem is, when I try to print a 6"x4" photo at the highest quality settings from a Windows PC via SAMBA, the printer will start up, give the message "Now printing...", feed the photo paper in, but it doesn't actually start printing.  If I check the print queue using lpq, the job is shown with the status "Active".  This never changes.

The only reason I can come up with for the photo not printing is that it's a big print job, and CUPS is struggling with it.  I don't have any restrictions set on the size of print jobs allowed.

Can anybody help with this?

Thanks in advance,

---

