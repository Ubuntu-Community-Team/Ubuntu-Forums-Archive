---
title: "OCR of Scans"
date: 2021-03-03
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2021-03-03
I have some scans and would like to convert them to PDFs with text. What software can do that? It would need to do OCR of the text in the document.

---

### Post by blackbird34 on 2021-03-03
You can install PDF Xchange Viewer via Wine (or PlayOnLinux, which is Wine in an easy wrapper) 

[https://www.tracker-software.com/product/pdf-xchange-viewer/download?fileid=445](https://www.tracker-software.com/product/pdf-xchange-viewer/download?fileid=445)

There's also an app called OCRFeeder in the repositories which is a frontend for the famous OCR engine Tesseract. 

Of course success and quality of the character recognition depnds on the quality of your scans.

---

### Post by ajgreeny on 2021-03-03
Tesseract has become much better and easier to use than it used to be when I first used it and I have had great success with it after scanning text from pages in books.

You must scan at a high resolution, as high as you can afford to (minimum 300 but better at 600 dpi) and save the image as png, jpg or any other image type; the need to save as a tiff has now been removed.

My main query is what will you use to create a PDF that is not just an image, ie, a PDF that contains the text which is what you say you need as there is little point scanning an image, producing a text file using OCR, then from that text file either saving as or printing as another PDF which depending on what creates it, might turn out to be just another image.

---

### Post by rsteinmetz70112 on 2021-03-03
I have the scans, but not the originals so I have to work with what I have. On Adobe Acrobat you can OCR a pdf and add searchable text to the pdf, some scanning programs have similar features. I have found a program called ocrmypdf which is a command line tool. It is supposed to take an input pdf and add a text layer for searchable text to an output pdf. I've installed it from the repositories and it uses tesseract but haven't really tried it out.

---

### Post by TheFu on 2021-03-03
**gscan2pdf** is what I use.  The OCR is highly dependent on the quality of the scan and NOT having funky fonts used. Different OCR engines are supported.  Generally, I only ensure about 10 keywords are correct in the OCR stuff to find the documents later when searching.  The text gets placed "under" the scanned image to make PDF search work.

---

