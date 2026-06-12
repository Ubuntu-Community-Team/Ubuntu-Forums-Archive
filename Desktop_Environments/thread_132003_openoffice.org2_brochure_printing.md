---
title: "openoffice.org2 brochure printing"
date: 2006-02-17
forum: Desktop Environments
---

### Post by dschaller on 2006-02-17
Can someone tell me if brochure printing is fixed yet in openoffice.org2 writer? Right now, I'm still using 1.1.5 because I need this feature.

---

### Post by glennr on 2007-08-13
I'm using Fiesty and this bug still appears to be there. However I haven't updated for a few months so it may be fixed by now.

A workaround is to use some of the ps tools. 

First export your document as a pdf then use a command like this one:

pdftops file.pdf - | psbook | psnup -2 | ps2pdf - | cat > brochure.pdf

You may need to add parameters to psbook and psnup for scaling etc, see man pages.

Reference: [http://ospublish.constantvzw.org/?p=90](http://ospublish.constantvzw.org/?p=90)

---

### Post by DonA on 2008-02-25
I am having an issue with Brochure printing from OpenOffice 2.3 writer.  I'm not sure if it is the same bug as described in this thread, but maybe it's similar.  Here's what I've got:
[LIST]
[*]Dell 1505n Laptop running Ubuntu Gutsy
[*]HP PhotoSmart C6280 Printer
[*]HPLIP 2.7.12
[/LIST]

With my 40-page document open in OO Writer, a page preview looks OK.  But when I do a print to file, or actually do a print, the pages are correctly ordered; however, the print is tiny.

Any ideas?  Is this an OOo issue, an HPLIP issue, an Ubuntu issue, or maybe something else?

Thanks:   ..DonA

---

### Post by Kurapika on 2008-04-24
Brochure Printing on the internet is as simple as 1, 2, 3. You search in Google, Yahoo, MSN or other search engine: [brochure printing]("http://www.squidoo.com/brochure-printing"), then comes all the shops offering brochure printing service.

PSPrint for example, they offer full range of service. Full Color Postcard Printing, Brochures, Stickers, Calendars and More!


But is the process really that simple?

---

