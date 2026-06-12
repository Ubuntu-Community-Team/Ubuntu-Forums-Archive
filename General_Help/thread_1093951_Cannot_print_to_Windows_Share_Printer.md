---
title: "Cannot print to Windows Share Printer"
date: 2009-03-12
forum: General Help
---

### Post by pieronip on 2009-03-12
Hi

When I try to add a Windows shared printer to Intrepid I can neither see the shared printer by browsing nor add it by specifying its location (*smb://domain/server/printer*).  There is no problem in accessing Windows shared folders.  The error message on trying to 'verify' the printer is
> 
The print share is not accessible

Any advice?

Many thanks.

---

### Post by plucky on 2009-03-12
Open **System > Administration > Printing > Server > Settings** and tick the box that says "Show printers shared by other systems".

Then try to add a new printer and see what it finds.

Otherwise checkout this [link](https://help.ubuntu.com/community/WindowsXPPrinter)


Good Luck

---

### Post by theozzlives on 2009-03-12
Right-click on your printer and make sure it's being shared.

---

