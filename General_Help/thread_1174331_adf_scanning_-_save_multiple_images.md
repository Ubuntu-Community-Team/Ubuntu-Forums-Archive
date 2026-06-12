---
title: "adf scanning - save multiple images"
date: 2009-05-30
forum: General Help
---

### Post by MrLobster on 2009-05-30
I'm try to use my ADF scanner (HP Officejet J4550) to save each page as a separate .png image.  I believe I have set the settings up properly in XSane.  It does seem to scan all the documents but the program only winds up saving the first page.  Is there anyway to get this to work properly?

---

### Post by stinger30au on 2009-05-30
piece of cake, you need the right software first

fireup shell and type in

sudo apt-get install gscan2pdf

heres the homepage for it

[http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)


one you start it up you can scan the pages you want and save them as individual files in what ever format you want or save to pdf as well

hope this helps

---

### Post by MrLobster on 2009-05-30
Worked perfectly, thanks!

---

