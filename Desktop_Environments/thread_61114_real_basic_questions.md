---
title: "real basic questions"
date: 2005-08-30
forum: Desktop Environments
---

### Post by nancylee on 2005-08-30
just loaded ubuntu onto an old laptop.  wondering about dial up companies that will work.  also how to load printers when the printer only supports mac and windows.  thanks for your help.

---

### Post by DJ_Max on 2005-08-30
It's more dependant on your modem then the dial-up company, which is usually OS independant.

As far as printers, lots. If you're used OS X, you'll know it comes with quite a few drivers, even old printers that never supported OS X, the same is with Linux.
[http://www.linuxprinting.org](http://www.linuxprinting.org)

---

### Post by shakin on 2005-08-30
The easiest way to install a printer is using kcontrol's printer wizard.

```
$ sudo apt-get install kcontrol
$ sudo kcontrol
```

Under Peripherals there is a Printers option. Go to Add Printer and the wizard will walk you through it. If you don't have a printer yet you can use the list of supported printers in the wizard to find which ones are supported.

---

### Post by DJ_Max on 2005-08-30
Kcontrol is for KDE. To install it on gnome it requires 104mb of files.

GNOME has a program to add printers as well.

System >> Administration >> Printers

It has a wizard as well. It will try to auto-detect your printer, if it's turned on of course.

---

