---
title: "How do I get my Windows/Mac scanner/printer to work in Ubuntu?"
date: 2005-12-11
forum: General Help
---

### Post by autonomy on 2005-12-11
I didn't find a thread on this.

---

### Post by kahping on 2005-12-11
If Ubuntu supports it, then it should Just Work ;-)

If you're having problems, it would help the forum members to help you if you could provide at least a brand and model of printer/scanner you're having problems with.

---

### Post by autonomy on 2005-12-11
Thanks, I don't think it works. I've just tried to print a text document, but it's not doing anything; so the brand is Epson and the model is Stylus CX5400.

---

### Post by az on 2005-12-11
[http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX5400](http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX5400)

You need to have the cupsys-driver-gimpprint installed.  Offhand, I do not know it is installed by default.

" Multi-function device: Printer, Scanner, Copier.

The printing engine is compatible to the one of the Epson Stylus C84"

[http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C84](http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C84)

---

### Post by autonomy on 2005-12-11
I have foomatic-db-gimp-print, and no other gimp-print showed up in Synaptic. I could download gimp-print from their sourceforge page, and they also have packages for debian and others in the archives; but I couldn't find the archives. This is the only thing keeping me from deleting my Winders partition.

---

