---
title: "Weirdness with cups-pdf and Acrobat Reader in Jaunty"
date: 2009-05-03
forum: General Help
---

### Post by dwasifar on 2009-05-03
I use cups-pdf to print pdfs from legacy applications.  It worked fine in Intrepid, but in Jaunty for some reason the results look awful when viewed in Adobe Reader 8; the fonts are all pixelized.  If I print the file (to paper) from within Adobe Reader, however, the resulting print looks fine.  Only .pdfs created in Jaunty have this problem; older files created with cups-pdf in Intrepid view and print fine in Jaunty.  Other viewers don't display the problem, either; Document Viewer and Okular look more or less OK.

So to sum up the problem:

PDF files, created with cups-pdf in Intrepid, display and print fine in Jaunty using Document Viewer, Okular, and Adobe Reader.

PDF files, created with cups-pdf in Jaunty, display and print fine in Jaunty using Document Viewer or Okular, print OK using Adobe Reader, but display poorly using Adobe Reader.

Anyone else?

---

### Post by cajunlibra on 2009-05-04
I've used it in previous versions but at th moment, it isn't working.  I can't find where the files are output.

---

### Post by dwasifar on 2009-05-04
Usually they go to the /home/[username]/PDF directory.  They will either be named for the file you're printing, or _stdin_.pdf.  If you don't have that directory, create one and see if that makes it work.

---

### Post by cajunlibra on 2009-05-04
Yeah I know.  In the past that worked, but not now.  I even created the PDF folder, it remains empty.  I have also searched for the files and got nothing also.

---

### Post by dwasifar on 2009-05-05
Do you get the "print completed" notification in the upper right corner of the desktop?  Maybe it's just failing.

---

