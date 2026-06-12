---
title: "Printer problems in KDE"
date: 2009-06-03
forum: Desktop Environments
---

### Post by sripplinger on 2009-06-03
I'm having printer issues in Kubuntu 9.04.  First off, I am able to install the printer (a networked HP Officejet 6300) and print a test page successfully.  However, after restart the printer is no longer available and must be reinstalled.

The other issue I've got is that I cannot print from Okular or Firefox.  I'm not sure exactly which applications I can print from and which I can not.  I just know that I can print a test page, but these two (while showing the printer) do not print.

---

### Post by mmarif4u on 2009-06-03
In my experience it does not print, because the problem is mostly the selection of the paper type under page settings. Did you tried to set the paper type in page format(something like that) to match the paper type of the printer.

Are you using CUPS for configuration of network printer?

---

### Post by sripplinger on 2009-06-04
Page setup was not the problem.  I was just using the printer setup application found under System Settings on the Advanced Tab in Kubuntu 9.04.  I had assumed that this was based on CUPS, but I do not know.  I did get it to work, however, by setting up the printer using CUPS in my browser (localhost::631).  Things seem good now.  I'm not sure why the KDE printer setup was having issues before.

---

### Post by gnulab on 2010-10-09
Same here, I have to configure my printer (normal printer & virtual printer, pdf) via

[http://localhost:631](http://localhost:631)

before it will print from any application.

Before that, setting up my printer via KDEPrint software 
(System Settings -> Printer Configuration), will result in successful Print Test Page (whether from [http://localhost:631](http://localhost:631) or from KDE Print), but not from any application. I have not tried command line printing (lpd) though.

After reading this post, I deleted all the printers from the KDEPrint software, then re-add them via [http://localhost:631](http://localhost:631)

Page setup was set up to match the settings in the KDE Print.

My system is KUbuntu 10.10.

Hope this helps to those had successfully added their printer but couldn't print from any application.
Henry

---

### Post by inobe on 2010-10-09
hplip gui tools, much easier controlling your hp printer with, install it.

---

