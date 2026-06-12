---
title: "Convert scanned pdf from 2- to 1-page per sheet"
date: 2009-02-09
forum: General Help
---

### Post by pixnaps on 2009-02-09
Hi, I have a book scanned to PDF, which is rendered in landscape with 2 (book) pages per sheet (pdf page). I would like to convert this so that each book page gets its own sheet in the PDF.

It seems like there should be an easy way to do this: in [Acrobat Pro]("http://help.adobe.com/en_US/Acrobat/8.0/Professional/help.html?content=WS58a04a822e3e50102bd615109794195ff-7bd5.html"), for example, you can double the scale of the PDF, and then "tile print" it across two "physical" pages (not really physical, since I plan to 'print to PDF').  But this feature isn't available in their free Reader, so it'd be great if it were possible to implement using open source tools instead.

([pdfposter]("http://pdfposter.origo.ethz.ch/") looks promising, except it looks like it may only work for single-sheet pdf input, and it's not included in any repositories, so would have to be compiled from source.)

If all else fails, I suspect it should be possible to write an ImageMagick script that (i) crops each half of each sheet in turn, then (ii) resizes and reorients each fragment thus produced, before finally (iii) recombining the output pages in the appropriate order.

Unfortunately, I lack the technical know-how to implement this :-p

The other idea I'm currently exploring is to merge the multipage pdf into a single ps file (does pdf2ps do this?), resize, then split it up using poster. (Not sure exactly how that works, though.)

Any suggestions?

---

### Post by photon_man62 on 2009-02-09
PDFposter looks like it can help you :D

You can get it here:
[http://pdfposter.origo.ethz.ch/download](http://pdfposter.origo.ethz.ch/download)

IN CASE YOU DON'T KNOW HOW TO INSTALL
Extract the folder to your desktop, navigate to it in the terminal and:

./configure
make
sudo make install

---

### Post by pixnaps on 2009-02-10
Ah, it does indeed allow for multi-page pdfs!  Very helpful, thanks.

---

### Post by CupofDice on 2009-12-09
How does this app actually work? What commands do I use?

---

### Post by pixnaps on 2009-12-15
e.g.
```
pdfposter -p2x1a4 landsc.pdf output.pdf
```

It's a bit unreliable though. I now prefer to use unpnup or (in windows) papercrop. (Google for more info on these.)

---

