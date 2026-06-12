---
title: "Question : Command Line to print any files to pdf"
date: 2009-06-05
forum: General Help
---

### Post by perigee on 2009-06-05
With pdf printer, is it possible to print any files (doc, xls ... ) to pdf format by using commands only (without open the files)?

---

### Post by cmnorton on 2009-06-05
lp -d pdf-printer-name file-name

where:
pdf-printer-name is the pdf printer defined in /etc/cups/printers.conf.

---

