---
title: "dvips makes trouble!"
date: 2006-02-15
forum: Desktop Environments
---

### Post by kalle314 on 2006-02-15
It seems there is something wrong with dvips in my two days old Breezy install.

I have lots of eps-figures made in Metapost with embedded latex text.
I run 
latex myfile.tex
dvips myfile.dvi
ps2pdf myfile.ps
to get a pdf-document, but in the postscript document (and the pdf) the text in the images are gone!
Hence there must be something wrong with dvips.

I have had no trouble with text in eps-figures in Hoary,
and I had no trouble with the file described above when I did run it in Suse.

---

### Post by neoflight on 2006-03-15
[QUOTE=kalle314]It seems there is something wrong with dvips in my two days old Breezy install.

I have lots of eps-figures made in Metapost with embedded latex text.
I run 
latex myfile.tex
dvips myfile.dvi
ps2pdf myfile.ps
to get a pdf-document, but in the postscript document (and the pdf) the text in the images are gone!
Hence there must be something wrong with dvips.

I have had no trouble with text in eps-figures in Hoary,
and I had no trouble with the file described above when I did run it in Suse.[/QUOTE]

its too late to reply i guess....still....
what program are u using to view those ps and pdf files....did u try pdflatex using .pdf figures? 
could you view those when using xdvi?  and the ps file using gv?

---

