---
title: "hplip c5280 not found usb"
date: 2009-02-13
forum: General Help
---

### Post by paul94 on 2009-02-13
Running Feisty Fawn on an old pc with 256Mb ram. Loaded hplip-2.8.12 to run hp c5280. Loaded with a few sub dependencies errors (scanimage +) made and installed then printed test page ok.  Then I get Device communications error Code 5012. Running lsusb does not find the printer but does find the other usb device (ADSL Modem).
Please can anyone help.

---

### Post by fragos on 2009-02-14
Run "hp-check" in a terminal. NOTE if there's nothing in the scanner it will complain about that but it's not important. You're only interested in the printing related messages.

---

### Post by paul94 on 2009-02-14
Thank you for your response. I have now printed successfully. The printer has a nice green tick in the Printer Box but still 'lsusb' does not show the printer. I can live with this for now. The card reader shows up as well. Can transfer images to system. Thank you again.[http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

