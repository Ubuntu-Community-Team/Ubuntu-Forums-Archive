---
title: "Printer Epson C46 not detected"
date: 2005-06-07
forum: Desktop Environments
---

### Post by Alanm on 2005-06-07
My Epson C42 has just given up, but my new C46 is not detected can anyone help? Although using Mandrake for a few years new to Kubuntu.

---

### Post by coolclassic on 2005-06-08
Try: [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) their drivers might make it easier.

---

### Post by Alanm on 2005-06-10
[QUOTE=coolclassic]Try: [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) their drivers might make it easier.[/QUOTE]
 [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) does not seem to cover C46. However Epson support suggested [http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html). I downloaded the rpm and then converted to a .deb using the package alien i.e. commard 
sudo alien pips-sc45_46s-cups-2.6.2-2.i386.rpm
Then installed with sudo dpkg --install 'pips-sc45-46s-cups_2.6.2-3_i386.deb'
Then do an add printer using the Printing manager and CUPS

---

