---
title: "Document to Image Conversion"
date: 2009-06-03
forum: General Help
---

### Post by apparle on 2009-06-03
I have a Document in .docx or .doc or .odt or .pdf format.

I want to make JPEG image for each page, but since it has around 1000 pages, print screen is useless.

Is there any direct tool or software or any method. Please help

---

### Post by apparle on 2009-06-03
I just saw that open office can save prints to file in the form of .ps files............so any way to convert this .ps file into multiple .jpg files??
Can I control the resolution

---

### Post by t0p on 2009-06-03
You can open .pdfs in the gimp.  Then you can convert to .jpg or whatever.

---

### Post by kaibob on 2009-06-03
> **apparle said:**
> I have a Document in .docx or .doc or .odt or .pdf format.

I want to make JPEG image for each page, but since it has around 1000 pages, print screen is useless.

Is there any direct tool or software or any method. Please help
You can use the Imagemagick convert utility to convert PDF to JPG. 

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

I don't know of any direct method to convert ODT or DOC files to JPG. Lacking any direct method, I would open the file in OpenOffice and then export it to PDF, which could then be converted to JPG with Imagemagick. I'm not familiar with DOCX.

---

### Post by s.fox on 2009-06-03
> **kaibob said:**
> You can use the Imagemagick convert utility to convert PDF to JPG. 


Hi,

I do a fair amount of that and it maybe of use to you know that sometimes image quality sometimes suffers if the pdf is password  protected.

-Ash R

---

