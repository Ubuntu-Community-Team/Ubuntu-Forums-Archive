---
title: "&quot;Print to File&quot; Problem"
date: 2009-01-16
forum: General Help
---

### Post by fmzw on 2009-01-16
The function works well. Only with the output of reaaally big pdf files. Anybody knows why? How can I adjust some parameter to make this default printing function generate smaller files?

I used pdfcreator before under Windows, which is a very efficent printer driver and can generate really neat files. Does anybody know the substitute of it under Ubuntu? Thanks!

---

### Post by binbash on 2009-01-16
you can also use cups-pdf

---

### Post by fmzw on 2009-01-16
OK, I will try that. Thanks!

---

### Post by fmzw on 2009-01-17
I tried cups-pdf. Still the same size, very big.

Any idea that I can make the output pdf file smaller?

---

### Post by kaibob on 2009-01-17
The size of PDF files created by cups-pdf is determined, in part, by the -dPDFSETTINGS option in the cups-pdf.conf configuration file (see snippet below). Available settings are:

* **screen** selects low-resolution output similar to the Acrobat Distiller "Screen Optimized" setting (screen-view-only quality - 72 dpi images); 

* **ebook** selects medium-resolution output similar to the Acrobat Distiller "eBook" setting (low quality - 150 dpi images); 

* **printer** selects output similar to the Acrobat Distiller "Print Optimized" setting (high quality - 300 dpi images); 

* **prepress** (the default) selects output similar to Acrobat Distiller "Prepress Optimized" setting (high quality with color preserving - 300 dpi images).

The default setting is prepress; you can change this by uncommenting the GSCall line and changing the -dPDFSETTINGS setting. Be sure to make a backup of the cups-pdf.conf file before editing.

> CUPS-PDF.CONF SNIPPET:
### Key: GSCall
## command line for calling GhostScript (!!! DO NOT USE NEWLINES !!!)
## MacOSX: for using pstopdf set this to %s %s -o %s %s
### Default: %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s

# GSCall %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s

SOURCES:
[http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm](http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm)
[http://milan.kupcevic.net/ghostscript_ps_pdf](http://milan.kupcevic.net/ghostscript_ps_pdf)

---

### Post by fmzw on 2009-01-20
Thank you very much for this kindly explanation!! Finally I can "use" cups-pdf!

---

