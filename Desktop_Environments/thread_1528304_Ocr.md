---
title: "Ocr"
date: 2010-07-10
forum: Desktop Environments
---

### Post by manolomanolo on 2010-07-10
Hi to all.

I am trying to run any OCR application in Ubuntu but I have not been lucky.

I've tried to follow this guide:
[http://ciaolinux.myblog.it/archive/2008/07/10/riconoscimento-ottico-dei-caratteri-ocr-con-xsane.html](http://ciaolinux.myblog.it/archive/2008/07/10/riconoscimento-ottico-dei-caratteri-ocr-con-xsane.html)

with no luck. It explains how to do using xsane and gocr/tesseract.I am unable to install xsane2tess and I get the following error:

```
sudo dpkg -i --force-architecture xsane2tess_1.0-1guadausers1_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 229257 files and directories currently installed.)
Preparing to replace xsane2tess 1.0 (using xsane2tess_1.0-1guadausers1_i386.deb) ...
Unpacking replacement xsane2tess ...
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xsane2tess

```

Both tesseract-ocr and tesseract-ocr-ita are installed. No "tesseract" package is in the repos.

Any suggestion, please?
Thanks.

Ubuntu 10.04 64 bit

---

### Post by Steve603z on 2010-07-10
not sure exactly what you are trying to do with OCR, but I've always found "gscan2pdf" to be a nice GUI application for scanning documents.  However Tesseract isn't a very good OCR program, commercial OCR applications are typically better.  ```
sudo apt-get install gscan2pdf
``` might be a better solution for you and should be easier to install.

---

### Post by nmaster on 2010-07-10
why not use pdfocr? it works fairly well and it *very* easy to use

[http://www.ubuntugeek.com/howto-make-scanned-pdfs-searchable-ocr-using-pdfocr.html](http://www.ubuntugeek.com/howto-make-scanned-pdfs-searchable-ocr-using-pdfocr.html)

---

### Post by Steve603z on 2010-07-10
> **neal.m.master said:**
> why not use pdfocr? it works fairly well and it *very* easy to use

[http://www.ubuntugeek.com/howto-make-scanned-pdfs-searchable-ocr-using-pdfocr.html](http://www.ubuntugeek.com/howto-make-scanned-pdfs-searchable-ocr-using-pdfocr.html)

From the looks of it, he's scanning documents to OCR, so using gscan2pdf will most likely remove a few steps by allowing him to OCR as soon as he scans

---

### Post by manolomanolo on 2010-07-10
thanks for your replies.

I have been using gscan2pdf with both the gocr and tesseract engine but the result is very very bad.

On the other hand, pdfocr produced an output very similar to the input, the only difference is that the text is selectable. i can copy it but it pastes something other than the real words.

May be those programs are not useful with text hand written?

---

### Post by Steve603z on 2010-07-10
> **manolomanolo said:**
> thanks for your replies.

I have been using gscan2pdf with both the gocr and tesseract engine but the result is very very bad.

On the other hand, pdfocr produced an output very similar to the input, the only difference is that the text is selectable. i can copy it but it pastes something other than the real words.

May be those programs are not useful with text hand written?

like I said, Tresseract (and gocr) arn't that great, they have a hard enough time with text from books and stuff.  Even high grade commercial applications have a hard time recognizing even very neat handwritten notes.

I did some work setting up OCR hand written form processing in the past, we had to write some logic challenges into the programs to verify the data,
(for example: if (DOB_Month > 12) || (DOB_Day > 31) || (DOB_Year < 1900) then flag for review)

also, the if the OCR programs confidence wasn't that high, it would flag it for review itself.

One of the best commercial OCR applications out there (IMHO) is ABBYY FineReader (or their other applications) but unfortunately as far as I know they don't have a linux version.  And it's pretty expensive ($400 for the full "Professional" version, but they have an "express" version for $50)

---

### Post by AlexDudko on 2010-07-11
Try **cuneiform** - I use it for several months and am quite satisfied with it. It's a terminal application and it is in Ubuntu repositories.

---

### Post by Robbyx on 2010-10-27
Has anyone got Abbyy FR 9 to work under wine? I use VirtualBox but I am using Win2K so I can not update to FR 10.

---

### Post by Nalin x Linux on 2012-11-12
[B]Linux-intelligent-ocr-solution
[/B]
[http://code.google.com/p/linux-intelligent-ocr-solution/](http://code.google.com/p/linux-intelligent-ocr-solution/)

Lios is a free and open source software for converting print in to text using either scanner or a camera, It can also produce text out of scanned images from other sources such as Pdf, Image or Folder containing Images. Program is given total accessibility for visually impaired. Lios is written in python, and we release it under GPL3 license. Lios will work with Debian based operating systems. There are great many possibilities for this program, Feedback is the key to it

---

