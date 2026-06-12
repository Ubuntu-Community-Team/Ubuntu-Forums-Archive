---
title: "Font name in PDF and also PDF size.."
date: 2009-04-05
forum: General Help
---

### Post by BugBuster on 2009-04-05
I use cups-pdf a lot to print a lot of stuff from Firefox 3.0.8 into PDF documents using ghostscript 8.61 on Ubuntu Hardy 8.04.2.
Mine is completely up to date Ubuntu installation as of the day I write this post.

Recently I have noticed one thing that kind of annoys me..
When I print to PDF in Hardy the pdf file that is created does embed the fonts, however the names of the fonts do not appear correctly.
The font names appear as f-01...f02...etc that I dont quite like.

Also the size of the pdf file that is created is quite large some times 3 or more times the size produced by PDFCreator 0.9.6 with embedded fonts as well on Windows XP SP3 that have on another pc.

So would like to have any suggestions from people who might have tracked this issue.This does not seem to be a very serious issue but I would like to have it corrected as I want
my Ubuntu installation to be as perfect as possible.

---

### Post by kaibob on 2009-04-05
> **BugBuster said:**
> ...Also the size of the pdf file that is created is quite large some times 3 or more times the size produced by PDFCreator 0.9.6 with embedded fonts as well on Windows XP SP3 that have on another pc.......

The size of PDF files created by cups-pdf is determined, in part, by the -dPDFSETTINGS option in the cups-pdf.conf configuration file. Available settings are shown below. The screen setting does significantly reduce file size but at the expense of quality, as the resolution is quite low and fonts are not embedded.

I am not bothered by the cups-pdf file sizes, so I use all the default settings, including prepress. Just as a test, I used cups-pdf to create a PDF of this forum's front page. The file contained 223 KB, which does not seem excessive to me. 

* **screen** selects low-resolution output similar to the Acrobat Distiller "Screen Optimized" setting (screen-view-only quality - 72 dpi images); 

* **ebook** selects medium-resolution output similar to the Acrobat Distiller "eBook" setting (low quality - 150 dpi images); 

* **printer** selects output similar to the Acrobat Distiller "Print Optimized" setting (high quality - 300 dpi images); 

* **prepress** (the default) selects output similar to Acrobat Distiller "Prepress Optimized" setting (high quality with color preserving - 300 dpi images).

I don't have any information on the names of embedded fonts, although I did confirm that the names of embedded fonts are as you describe. 

SOURCES:
[http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm](http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm)
[http://milan.kupcevic.net/ghostscript_ps_pdf](http://milan.kupcevic.net/ghostscript_ps_pdf)

---

### Post by kaibob on 2009-04-05
Post deleted by Kaibob

---

