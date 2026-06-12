---
title: "cups print to png jpg jpeg?"
date: 2008-12-26
forum: General Help
---

### Post by k7my on 2008-12-26
cups can print to pdf, but how to print to image format like png jpg jpeg ???

---

### Post by ibuclaw on 2008-12-26
My first thought is that I don't believe this is possible directly using cups, but you can convert PDF Files into jpgs/pngs/gifs/etc once created.

Regards
Iain

---

### Post by scandido on 2008-12-26
Try looking at the command 'convert' to do this easily. It's as simple as

convert document.pdf document.png

Good luck.

---

### Post by kaibob on 2008-12-26
> **k7my said:**
> cups can print to pdf, but how to print to image format like png jpg jpeg ???

Cups-pdf uses ghostscript to produce PDF files, and ghostscript supports various -sDEVICE options including PNG, JPG, and TIF. So, it would appear possible to print to one of these formats, although I've never heard of anyone actually doing this. Look at the "### Key: GSCall" section of the /etc/cups/cups-pdf.conf configuration file if you want to pursue this further.

Cups-pdf also supports post processing and that would be an alternative. Just print to PDF and then immediate convert to whatever format is desired. It's a lot of work to configure this. 

Unless this is something you're going to do on a regular basis, I agree with the above postings that the convert utility is the way to go.

---

### Post by k7my on 2008-12-27
thx guys, I will try use convert, but really hope that got something just like cups-png/cups-jpg/cups-image :) or something like firefox add-ons (Abduction!/Screengrab!)

---

### Post by gregb49 on 2009-02-14
> **k7my said:**
> thx guys, I will try use convert, I've found that even using the highest quality settings, there is an appreciable loss of quality using ```
convert
``` to convert a PDF to a PNG. I'm stuck with a PDF file from OpenOffice Writer 2.4 but have found that The GIMP will convert PDFs with no loss of quality, if you experiment with the import settings, ie push the resolution up several times. Then the image can be saved as PNG, JPG or whatever. 

I know it's not the answer to the question, but until I can find a way install OOo 3.1, with its improved Draw - Image - Export capabilities, this seems an acceptable work around.

Greg

---

### Post by saqibali on 2011-10-02
Yea quality using convert is terrible. I have to use GIMP for the conversion :(

---

### Post by mcduck on 2011-10-02
> **gregb49 said:**
> I've found that even using the highest quality settings, there is an appreciable loss of quality using ```
convert
``` to convert a PDF to a PNG. I'm stuck with a PDF file from OpenOffice Writer 2.4 but have found that The GIMP will convert PDFs with no loss of quality, if you experiment with the import settings, ie push the resolution up several times. Then the image can be saved as PNG, JPG or whatever. 

I know it's not the answer to the question, but until I can find a way install OOo 3.1, with its improved Draw - Image - Export capabilities, this seems an acceptable work around.

Greg

Did you also set the desired input DPI value when doing the conversion? You really need to do that when converting to/from PDF, as otherwise convert defaults to standard display setting of 96DPI, while you probably want something around 300DPI at least.

With correct options convert does excellent work when converting to/from PDF.

---

### Post by gregb49 on 2011-10-02
> **mcduck said:**
> Did you also set the desired input DPI value when doing the conversion?No, I don't think I did, thanks. Since the time of the last posting, I've been using OOo3 successfully to achieve the conversion.

---

### Post by mcduck on 2011-10-03
> **gregb49 said:**
> No, I don't think I did, thanks. Since the time of the last posting, I've been using OOo3 successfully to achieve the conversion.

Ok, then that's most likely the reason for low quality. The DPI can be set using the "-density" option, and it seems even the 96DPI I remembered was too much, the default is only 72DPI...

[http://www.imagemagick.org/script/command-line-options.php?ImageMagick=f6d80r52d2br0mbk8d2tmrrbe7#density]("http://www.imagemagick.org/script/command-line-options.php?ImageMagick=f6d80r52d2br0mbk8d2tmrrbe7#density")

---

### Post by gardengxc on 2012-07-21
A realiable method for making good quality JPGs or other image formats is gimp. Gimp can import from PDF and the resulting quality is superb. Much better then other ways I've see.

It's 2 extra steps but you can't argue with the quality of the resulting pics.

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

