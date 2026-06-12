---
title: "HP Business Inkjet 1200 HPLIP mess"
date: 2007-07-12
forum: Desktop Environments
---

### Post by fdimmling on 2007-07-12
I bought a HPBusiness Inkjet 1200 USB printer because HP printers  are regarded the best supported in Linux. Printing worked, but the hp-toolbox could not find my printer, error message 'model not supported'. 
Since the Feisty version 1.7.3 of hplip is fairly outdated I downloaded the latest version 2.7.6 for Ubuntu 7.04 from the HP website and installed it. The printer was not found either, same error as before. However printing was defective, all blank lines were removed regardless if printing from OpenOffice, a ps or pdf file. I uninstalled hplip 2.7.6  and reinstalled the Ubuntu version, but now all print jobs were immediately stopped in CUPS. 
I could not manage to make CUPS printing the jobs and finally reinstalled Ubuntu :mrgreen: Printing now works again, printer tools still missing. 

Rather frustrated

Friedrich

---

### Post by linuxwizard on 2007-07-12
I know the first time I opened the HP Toolbox I got a error saying I need to install   python qt3 in order to use it. 2 other packages was also installed libqt3-mt,  python-sip4. After install HP toolbox worked.

---

### Post by fdimmling on 2007-07-13
HP Device manager is starting and showing the printer, but with a red cross and grayed out. No details are shown, no functions available, refresh does nothing.

Friedrich

---

### Post by linuxwizard on 2007-07-13
Now that the printer shows up in the HP toolbox. Make sure it is plugged in & turned on.

According to this that printer should work perfect.
[http://www.openprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_1200](http://www.openprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_1200)

What I would do now go back over your setting make sure everything is setup right. Look over this on setting it up. I know it says Dapper but just over look that. Start at  Add a USB/LPT printer using gnome-cups-manager don't worry about where it tells you to open up a ternmal and add lines skip. Make sure driver is HPLIP.
[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)


I am running 3 HPs printers. They all work better on Ubuntu/Kubuntu then they ever did in windows.

---

### Post by fdimmling on 2007-07-14
I know that this model should be supported perfectly - but the hp-toolbox obviously doesn't know it. Starting hp-toolbox gives the message:

 error: Unsupported model: Business_Inkjet_1200

Friedrich

---

### Post by linuxwizard on 2007-07-14
Try Issue #1
[http://hplip.sourceforge.net/troubleshooting/toolbox.html](http://hplip.sourceforge.net/troubleshooting/toolbox.html)

I doubled checked here to see if any notes or specific settings needed for that printer none should just work
[http://hplip.sourceforge.net/supported_devices/inkjet.html](http://hplip.sourceforge.net/supported_devices/inkjet.html)

I don't know what else to tell you. If you installed those packages I posted , made sure plugged in & on , went back over the setup, just don't know what else we are missing.

---

### Post by fdimmling on 2007-07-15
I had checked all this before. I will be away for the next few weeks and I will post the problem to the mailinglist after my return. 

Thanks for your help

Friedrich

Obviously I am not the only one who has this problem, see [http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg03607.html](http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg03607.html)

---

