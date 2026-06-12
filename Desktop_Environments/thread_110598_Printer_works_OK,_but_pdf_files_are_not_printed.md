---
title: "Printer works OK, but pdf files are not printed"
date: 2005-12-31
forum: Desktop Environments
---

### Post by NRios on 2005-12-31
Hello!

I've got a desktop and a laptop running breezy, and a Samsung ML1710 laser printer. Both computers print fine from OpenOffice or the "lpr text_file" command in bash. Both Evince and Adobe Acroread show pdf files just fine in both computers. However, I cannot print normal pdf files on either computer with Acroread or Evince, nor by using lpr from the command line.

If I choose the ML1710 printer in Evince's print dialog, nothing is printed (or even ever put in the print queue).

If I choose "create pdf document" in Evince's print dialog, it complains that pdf file creation is not supported.

If I choose "generic postcript" in Evince's print dialog and I print to a file, a ps file is generated that only contains a blank page.

If I choose "generic postcript" in Evince's print dialog and I print to lpr, nothing happens, just as when printing with lpr from Acroread or the command line.

Anybody there can help me?

Thanks!

.Nacho.

---

### Post by Sef on 2006-01-04
What driver did you download?

Are you using a USB or parallel port?

From linuxprinting, here is what they say about your printer:

[http://linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1710]("http://linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1710")

---

### Post by el3ktro on 2006-01-30
I have the same problem with a Kyocera FS-1010 laser printer. Printing from OOo, GEdit etc. works fine, even over the network, but Evince won't print any PDFs. Any solution yet?

Tom

---

