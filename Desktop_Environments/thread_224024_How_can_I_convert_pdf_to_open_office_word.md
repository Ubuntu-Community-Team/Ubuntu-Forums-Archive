---
title: "How can I convert pdf to open office word"
date: 2006-07-27
forum: Desktop Environments
---

### Post by mittomus on 2006-07-27
How can I convert a PDF file to Open Office so I can edit it?

---

### Post by avtolle on 2006-07-27
Disregard.

---

### Post by aysiu on 2006-07-27
Use KWord, not OpenOffice.

---

### Post by john rose on 2006-08-06
I also want to do this. The best way that I've found so far is to use the standard Unix copy facility i.e. to copy: just drag with the left mouse button pressed from the beginning to end of the document) when the document is displayed by opening it with xpdf; to paste: use the standard Unix paste facility (i.e. click on the start of a new OO Writer document with the mouse left button & then click the mouse wheel / middle mouse button. This document will then have paragraph breaks inserted in the places where the lines break in the xpdf display. I then used 'Edit Find/Replace' (in Writer) with 'Search for' as ^. 'Replace with' as a space followed by $ (this inserts a space character before each paragraph break) and 'Regular expressions' check box ticked (click on More to see Regular expressions') to insert a space character before each paragraph break i.e. between words. I then used 'Edit Find/Replace' (in Writer) with 'Search for' as $ 'Replace with' as nothing and 'Regular expressions' check box ticked (click on More to see Regular expressions') to remove all paragraph breaks.  I then put in the required paragraph breaks by pressing the Enter key at the appropriate places.

John

---

