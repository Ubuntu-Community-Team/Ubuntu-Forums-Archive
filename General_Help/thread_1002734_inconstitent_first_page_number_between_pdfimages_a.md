---
title: "inconstitent first page number between pdfimages and unpaper"
date: 2008-12-05
forum: General Help
---

### Post by roy.nico on 2008-12-05
Hello everybody.

I scanned a book into a pdf document. For some reason, i want to apply unpaper to each of the pages. My method : 
$ pdfimages book.pdf page

This extracts all the pages to a file 
page000.pbm
page001.pbm ...

Then i want to apply 
unpaper (some options) page%03d.pbm modified_page%03d.pbm

This works great ... except that for mutiple files, unpapers starts with 001 whereas the output from pdfimages start from 000.
This means, thru this process, i loose the first page.

Does anyone know how to change the "first page number" for multiple file, either in unpaper or in pdfimages ?

Thanks a lot in advance for any idea .
Nicolas

---

