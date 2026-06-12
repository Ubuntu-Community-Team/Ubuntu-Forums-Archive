---
title: "Text Extraction From Scanned Documents"
date: 2009-05-11
forum: General Help
---

### Post by Patriot1776 on 2009-05-11
I wasn't exactly sure where to put this, whether it went into multimedia production or not.

I today got a HP printer/scanner/copier for the purpose of not only printing, but scanning typewritten pages as I'm an amateur writer and do my writing on a separate electric typewriter for limited distraction while I am writing.

I've just used gscan2pdf to scan and convert my first pages of typewritten text into PDF, but I still cannot pull the text itself out of the PDF for pasting into OpenOffice.  I need to know if there's any open source program available that can extract text from images, or am I going to have to use a different internal image format for my PDFs?  gscan2pdf is set to scan pages as JPEGs.

---

### Post by 987poiuytrewq on 2009-05-11
The site [http://groundstate.ca/ocr](http://groundstate.ca/ocr) does a good round up of OCR for Linux, and remember you can convert from one image type to another (including pdf) using ```
convert -format png scan.pdf
``` for example.

---

### Post by Patriot1776 on 2009-05-11
Okay, I got Tesseract installed.  When I select the OCR option in gscan2pdf, where does the OCR output go?

---

### Post by coffeecat on 2009-05-11
The other way is to make sure you have the ocr* package installed and then use Xsane (Applications > Graphics - comes with a default install) to scan the document. Set the scan mode to 'lineart' and resolution to 300 and scan. In the viewer windows that opens with the scan image, choose 'OCR- save as text' from the file menu. The text is saved as a plain .txt file which can be opened directly in OpenOffice.

Also, have a look at the package 'Okular' from the repositories. It's a very good pdf reader and you can select and extract images and text from PDFs with it.

However, if you want to get scans from your typewritten documents into OOo, the Xsane route would be much simpler than making PDFs as an interim step. I've tried it with my HP multifunction machine and it works fine. In fact I'm impressed with the accuracy of the gocr plugin. That, by the way, is why you need the 300 resolution. The results from the default 75 resolution are hopeless.

**Edit:** sorry - typo. I meant the gocr package.

---

