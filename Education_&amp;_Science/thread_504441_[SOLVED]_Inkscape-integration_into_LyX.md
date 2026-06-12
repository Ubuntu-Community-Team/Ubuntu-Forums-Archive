---
title: "[SOLVED] Inkscape-integration into LyX"
date: 2007-07-19
forum: Education &amp; Science
---

### Post by xilix on 2007-07-19
I want to be able to insert Inkscape-SVG-files directly into LyX. The goal is that LyX converts the SVG via an external converter into PNG for the preview and into PDF for the pdflatex-compilation. So I only have to store my SVG-files.

I followed this tutorial in the LyX-Wiki: [wiki.lyx.org/Tips/UseInkscapeSVGImages]("http://wiki.lyx.org/Tips/UseInkscapeSVGImages")

The preview is working, but the quality of my graphics in the pdf-file is very bad. It looks like LyX uses the PNG-file for the pdflatex-compilation. I also checked the temporary files in the /tmp/-folder and there was no pdf-file of the image. So LyX doesn't use the converter SVG->PDF. The converter itself (via inkcape-export) works in the shell... The same when I try SVG->EPS->PDF (with inkscape and epstopdf)

Currently I use LyX 1.4.3 and Inkscape 0.45.

I don't know what to do now. Anyone an idea?

---

### Post by ilanmg on 2007-07-19
> **xilix said:**
> I want to be able to insert Inkscape-SVG-files directly into LyX. The goal is that LyX converts the SVG via an external converter into PNG for the preview and into PDF for the pdflatex-compilation. So I only have to store my SVG-files.

I followed this tutorial in the LyX-Wiki: [wiki.lyx.org/Tips/UseInkscapeSVGImages]("http://wiki.lyx.org/Tips/UseInkscapeSVGImages")

The preview is working, but the quality of my graphics in the pdf-file is very bad. It looks like LyX uses the PNG-file for the pdflatex-compilation. I also checked the temporary files in the /tmp/-folder and there was no pdf-file of the image. So LyX doesn't use the converter SVG->PDF. The converter itself (via inkcape-export) works in the shell... The same when I try SVG->EPS->PDF (with inkscape and epstopdf)

Currently I use LyX 1.4.3 and Inkscape 0.45.

I don't know what to do now. Anyone an idea?


kjnsdfasdfasdf

---

### Post by kleeman on 2007-07-20
In my experience lyx (and tex) handle eps files best. Have you tried exporting your inkscape picture to eps (use the save as function)?

---

### Post by xilix on 2007-07-23
Of course that works. But pdflatex cannot handle eps-files. So they are converted into pdf-files. But that would not be a problem, because it works automatically. 
I want to insert SVG-Files into LyX because then I can click on "Edit" in the Image-Dialogue an the SVG-File will be opened in Inkscape. I can edit it and just save ist. All changes will be automatically inserted in LyX. That would be very convenient. But it doesn't work with the pdflatex-export.

---

### Post by Typhoon on 2007-07-24
Pdflatex can use .png files directly. I have always had good results with them.

In order to use them, it may be necessary to put the following line in the preamble:

\DeclareGraphicsExtensions{.png}

HTH,
Typhoon

---

### Post by xilix on 2007-07-28
> **Typhoon said:**
> Pdflatex can use .png files directly. I have always had good results with them.

In order to use them, it may be necessary to put the following line in the preamble:

\DeclareGraphicsExtensions{.png}

HTH,
Typhoon

OK, but I think it's a good principle to use vector-graphics if you already have them. This would be the last option I would choose.

---

### Post by kleeman on 2007-07-28
Couple of suggestions:

1) Try the 1.5 version for lyx and see if there is an improvement. I have debs elsewhere in the subforum.

2) I read the user documentation (embedded objects) and there is a claim in there that there is not yet an adequate svg--> pdf converter. If you feel otherwise it may be worth taking this up with the developers on the lyx-devel mailing list. The people there are pretty approachable.

---

### Post by xilix on 2007-08-04
> **kleeman said:**
> Couple of suggestions:

1) Try the 1.5 version for lyx and see if there is an improvement. I have debs elsewhere in the subforum.

Thank you very much. Now I've solved it. I don't really know if it works only with LyX 1.5.0. But it works.

Basically I followed the LyX-Wiki (replace EPS with PDF). But it only worked when I activated the checkbox before "vector-format" (or something like that. It is german) in the preferences under "file-format - SVG".

> **kleeman said:**
> 
2) I read the user documentation (embedded objects) and there is a claim in there that there is not yet an adequate svg--> pdf converter. If you feel otherwise it may be worth taking this up with the developers on the lyx-devel mailing list. The people there are pretty approachable.

IMHO the Inkscape pdf-export is OK...

Now my LyX rocks... :-)

---

