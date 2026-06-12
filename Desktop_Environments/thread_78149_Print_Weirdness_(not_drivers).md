---
title: "Print Weirdness (not drivers)"
date: 2005-10-17
forum: Desktop Environments
---

### Post by jpt2433 on 2005-10-17
I am running breezy, upgrade from hoary and I'm having some printing issues.  When I attempt to print files I'm either getting an all black page or a very strange looking terrible quality print.  So I tried printing to PDF then sending the PDF to a friend to print, but when I printed to PDF I noticed that the PDF looked awful.

The colors are off (it is supposed to be black/blue) and the quality in general is terrible, I've attached a screenshot of the pdf as it's too large to attach.  The terrible quality is exactly what it looks like when I print.

Since this happens when I print to a PDF (and printing a test page on my printer I'm confident it's not printer related, it even happens if I remove my printer from the system)

This is happening from Eye of Gnome, as well as Inkscape and gThumb.

---

### Post by MetalMusicAddict on 2005-10-17
Do you have acroread and acroread-plugins installed? They might have something to do with decoding the PDF.

---

### Post by jpt2433 on 2005-10-17
The PDF looks like it does in Evince and in Acroread, also since printing directly to the printer looks just like printing to the PDF, I don't think it's the PDF readers fault, I think that the PDF generation is where it's failing.

Essentially I'm pretty sure that I've narrowed it down to the printer system, seeing as Firefox can print fine.  Eye of Gnome and other apps that print through the Gnome print dialog seem to be the issue here.

---

### Post by jpt2433 on 2005-10-18
I've verified that this happens on a fresh install of breezy on a different machine, I've attached the SVG file, could maybe one other person verify this before I file a bug report.

Steps to reproduce:
1) open the following document in the default gnome image viewer
2) try to print using the built-in PDF printer
3) view the resulting PDF

the resulting PDF looks terrible, and this is what it looks like when printed too, if you want to waste a little bit of ink go ahead and print it to confirm

---

