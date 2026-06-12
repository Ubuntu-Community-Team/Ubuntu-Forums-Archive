---
title: "Export Presentation with animations to PDF"
date: 2010-12-30
forum: Education &amp; Science
---

### Post by tzjin anthony ks on 2010-12-30
Hi, All.

I have a presentation in OpenOffice with simple "appear" animations. On exporting to PDF, however, the slides have all the elements present. It is straightforward to copy slides, and add elements to simulate the "appear" effect, but maintenance becomes difficult.

I was wondering if anyone might know of a way to export slides with "appear" effects as multiple pages in a PDF.

Thanks.

Tzjin.

---

### Post by PGScooter on 2010-12-30
I don't think I understand the problem. The problem is when viewing the pdf with animations? I think that adobe reader is the only reader than can view animations (even simple ones). You can install the linux version and try that.

---

### Post by tzjin anthony ks on 2010-12-30
Hiya, PG

Let's see if I can rephrase:

I have a presentation with (for simplicity's sake) one single slide, and two images.

Image 1 is present as soon as the slide is displayed. On mouse click, the second image appears.

If I export this slide to PDF, I get a single page, with both images. Can openoffice somehow export this slide as two pages - page 1, with image 1 alone. page 2, with both image 1 and image 2 ?

Hope this is clearer. 

Alternatively, can I export animations in openoffice to the PDF?

Cheers.

---

### Post by PGScooter on 2010-12-30
ah, I understand now. I don't know the answers to either of your questions. If you can't export from word the animations maybe you can from a different program, but I have no idea what to suggest. Good luck!

---

### Post by Chronon on 2010-12-31
I don't know about OOo, but here's a method that may work for LaTeX:
[http://pages.uoregon.edu/noeckel/PDFmovie.html](http://pages.uoregon.edu/noeckel/PDFmovie.html)

Sorry it doesn't help you convert your existing presentation, but it could enable animated content in future PDFs prepared from LaTeX.

---

### Post by PC_load_letter on 2010-12-31
Just like chronon said, doing this trick in LateX, say using beamer, is a piece of cake. If you are not familiar with LateX you may try Lyx (in the repos) and use a beamer template for your presentation. When you're done, do a pdflatex and your pdf presentation will have the desired effect. 

Another solution (that do not involve LateX):
- make your presentation like an animation artist would, one page per frame. So on page 1 just put the first image, while on page 2 put the 2 images. 

Hope this helps.

---

