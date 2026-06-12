---
title: "Evince (and others) print too large"
date: 2009-05-22
forum: General Help
---

### Post by tpmoney on 2009-05-22
I have an odd issue attempting to print PDFs in jaunty. Up until a few days ago, I had evince properly printing a 2.25inx6.5in label to a remote label printer via CUPS just fine. I did have to set the "format for" option in the print settings and give it the proper paper size, but other than that, it was working fine. The file being printed is a multi page PDF with each page formatted for the printer size already. I could also print standard 8.5x11 sized documents to a different printer without having to alter the format for options

I then had to print a much larger document to a different printer, and in doing so, changing the format for options. Now when I try to print the labels again it prints in massive print size (bigger than even 8.5x11) and on multiple labels.

If I send the document via lpr to the printer, it prints proper size, albiet rotated 180 degrees. However, printing in evince or a few other pdf viewers (Okular and pdfViewer) yeild the same results, proper orientation, massive size.

Ay thoughts?

---

### Post by sedawk on 2009-05-22
Sounds somehow familiar ...
Here printing is often going for "letter" size although I changed it
in the default options again (and again (and again)).

What is the default paper format defined for the printer?
(System->Administration->Printing->...)
Try to create a new printer connecting to the same physical
printer and see if that helps.

---

### Post by tpmoney on 2009-05-22
Default media size is the same as the label and printout 6.25x6.5 so no mismatches there.

Trying a "new" printer yields no different results.

---

