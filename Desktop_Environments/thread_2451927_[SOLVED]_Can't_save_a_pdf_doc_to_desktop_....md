---
title: "[SOLVED] Can't save a pdf doc to desktop ..."
date: 2020-10-13
forum: Desktop Environments
---

### Post by dbee on 2020-10-13
I'm editing a pdf doc but i can't seem to save my edits. Also, when i do save the doc, it doesn't appear on GNOME desktop...

I've restarted GNOME ....

```
gnome-session restart
```

I can access the saved file through file manager and through bash but it doesn't appear on my desktop environment.

```
evince mynonappearingdoc.pdf
```

Seems to work fine. But the edits i've made to my pdf doc don't get saved.

I run ghostscript and get ...

```

$gs mynonappearingdoc.pdf

  **** This file had errors that were repaired or ignored.
   **** The file was produced by: 
   **** >>>> Mac OS X 10.13.6 Quartz PDFContext <<<<
   **** Please notify the author of the software that produced this
   **** file that it does not conform to Adobe's published PDF
   **** specification.

   **** The rendered output from this file may be incorrect.
GS>Error: /undefined in B
perand stack:
   --nostringval--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:727/1123(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--
Current allocation mode is local
Last OS error: No such file or directory
Current file position is 4
GS<1>


```

Also, the pdf viewer has seg faulted ...

---

### Post by TheFu on 2020-10-13
PDF files can't be edited.  PDF is a write-once format.
PDF does support "annotations" which are an overlay to the file.  

I didn't know that evince supported any annotations. I've been using Okular.  With Okular, we "export" to a new PDF file our annotations with the original PDF. [https://askubuntu.com/questions/1529/how-can-i-highlight-or-annotate-pdfs](https://askubuntu.com/questions/1529/how-can-i-highlight-or-annotate-pdfs)

Perhaps I'm being to specific about the term "edit" vs import --> change --> export?  LibreOffice can open and modify some PDF files, but it depends on the exact way the PDF was created and how "clean" the PDF data is.  PDF sources can come from almost anywhere. Sometimes all the PDF creation tool can to is accept an image and store that for a page. No text. No numbers, just "place image type=XYZ, at location 0x0, and scale to 51.564% original size.  There's no way to edit a file like that. It would be easier to convert the PDF to 1-image per page, then run OCR and hope for the best.  I do that with some of my PDFs, because images cannot be searched, but if we place the OCR's text (or at least some keywords) **underneath** the image, then searching could work for some people.
If the goal is to edit the document, don't use PDF.  PDFs should only be used when it is truly write-once and where page layout controls are absolutely mandatory.  For the rest of us, HTML or RTF or ODS are better, open, formats if there are images involved.  Even better formats are non-page stuck methods, like plain text or markdown (of some sort).  Markdown/texttile can easily be converted to almost any other document format using pandoc.  </rant> sorry about that.  I worked in document management and document creation for almost a decade and saw some really poor choices related to data formats which took away much of the power that text provides for free.

Encrypted PDFs are more hassle.

As for the gnome question, sorry, can't help. I don't use gnome, but I thought the Gnome3 guys decided we wouldn't be allowed to place files on the desktop.  That wasn't in their ideal workflow, so if that is something you want, some gnome3 addon will be needed, I suppose. [https://fedoramagazine.org/changes-files-gnome-3-28/](https://fedoramagazine.org/changes-files-gnome-3-28/) says Gnome 3.28 doesn't allow files on the desktop. For earlier versions: [https://askubuntu.com/questions/43246/how-to-configure-gnome-3-to-show-icons-on-desktop](https://askubuntu.com/questions/43246/how-to-configure-gnome-3-to-show-icons-on-desktop)

---

### Post by T6&amp;sfpER35% on 2020-10-14
i use [this](https://smallpdf.com/) site to "edit" or maybe [COLOR=#000000] "import --> change --> export" (whatever the difference is) PDF docs.[/COLOR]

---

### Post by grahammechanical on 2020-10-14
I do not think that the Gnome developers want us to have icons on the desktop. If we install Gnome Tweak tool we can enable a setting that will let us put icons on the desktop. Or we can install a Gnome extension from the Gnome web site. In the past community produced Gnome extension would often break when Gnome shell was upgraded.

[https://itsfoss.com/gnome-tweak-tool/](https://itsfoss.com/gnome-tweak-tool/)

Regards.

---

### Post by CelticWarrior on 2020-10-14
> **grahammechanical said:**
> I do not think that the Gnome developers want us to have icons on the desktop. If we install Gnome Tweak tool we can enable a setting that will let us put icons on the desktop. Or we can install a Gnome extension from the Gnome web site. In the past community produced Gnome extension would often break when Gnome shell was upgraded.

[https://itsfoss.com/gnome-tweak-tool/](https://itsfoss.com/gnome-tweak-tool/)

Regards.

This^^^
Honestly, the simple solution is NOT do that. I know many people do but they shouldn't. The Desktop was never intended for that purpose and the more stuff you put there (in OSes and/or DEs where it's still allowed) the slower the boot process will be. Adopting better practices - proper personal files organization - is much better, just save the file somewhere else.

---

### Post by dbee on 2020-10-19
Ok thanks

---

