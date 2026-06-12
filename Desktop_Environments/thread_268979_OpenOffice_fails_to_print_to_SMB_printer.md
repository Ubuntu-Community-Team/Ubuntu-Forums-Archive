---
title: "OpenOffice fails to print to SMB printer"
date: 2006-10-01
forum: Desktop Environments
---

### Post by plc on 2006-10-01
Hi All,

I have Ubuntu Dapper installed on my machine at work.  The only barrier to me now using it is that OpenOffice will not print to a Windows Network (HP 2100) printer.

I added two printers using the System > Administration > Printers GUI.  No problems there, I could print test pages without issue.  I can also print web pages from Firefox. 

But when I try to print any OpenOffice document the print job disappears.  The Print window that comes up in OpenOffice lists both printers as an option, but interestingly after the default printer is selected the next line identifies the printer name with a CUPS prefix.  Does this mean that it is mistaking the Windows (SMB) Printer as a CUPS printer?  Do I need to add the printer in CUPS?  I wondered if it was an OpenOffice issue since Firefox works.  However no forums seem to be listing major problems with OpenOffice using SMB printers.

Unfortunately I have not installed any updates as I am still waiting for my employer to bypass our proxy for apt-get updates since no proxy trickery with apt-get will make it work. So I am unsure if this was fixed with an update.

Has anyone else had this problem with printing to Windows printers from OpenOffice?

Thanks in advance,
Paul

---

