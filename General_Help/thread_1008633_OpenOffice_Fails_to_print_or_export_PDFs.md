---
title: "OpenOffice Fails to print or export PDFs"
date: 2008-12-11
forum: General Help
---

### Post by chodgson on 2008-12-11
I'm using OpenOffice 2.4.1 on Ubuntu 8.04 (using the OO packages from Ubuntu). I originally had no problems printing with OO. At some point after upgrading to 2.4.1 from 2.4, and changing printers, printing has stopped working from OO. All other applications have no problem printing (PDF viewer, text editor, thunderbird mail). Both the old and new printers were network-based.

I've watched the CUPS log as I try to print from Writer, and it does several cups requests including asking for the printer's .PPD file - but never actually queues a print job. No errors are logged by CUPS. Writer behaves as if it has successfully printed, there is no error message given. But since the job never gets queued, I get no print queue icon in my tray and nothing prints.

My initial attempt at a work around was to export to PDF and print the PDF - however, only the correct number of blank pages get exported to the PDF.

I have tried other network printers, I have re-installed OO, I've even downgraded back to version 2.4.0, all to no effect. Because there is no error message or log from OO, I have nothing to go on to debug further - can anyone tell me where to look to find out what is happening? Or give me anything else to try?

---

### Post by linux_tech on 2008-12-11
One option is to try cups-pdf-
[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/download.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/download.shtml)

---

### Post by bhold on 2008-12-14
I suddenly lost the ability to print to a network printer with OO Writer 2.4. 

Googled around & found the following tip,it worked for me: In OO Writer,
Tools -> Options -> OpenOffice.org -> General... check the Use OpenOffice.org dialogs checkbox. 

This worked for me, although I am not sure exactly why it worked after reading about this bug...
[https://bugzilla.redhat.com/show_bug.cgi?id=213119](https://bugzilla.redhat.com/show_bug.cgi?id=213119)

Anyway, hope this helps, good luck.

---

