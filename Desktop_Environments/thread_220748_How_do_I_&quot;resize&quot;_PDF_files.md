---
title: "How do I &quot;resize&quot; PDF files?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Sunnz on 2006-07-22
I know that you could zoom in and out easily in a PDF file... but I am trying to publish a book now, which the publisher needs the PDF file I have to be in the exact size their printers required...

What program will I be able to resize a PDF file?

---

### Post by aysiu on 2006-07-22
Use ImageMagick. ```
sudo aptitude update
sudo aptitude install imagemagick
mogrify -resize 800x600 file.pdf
```

---

### Post by Sunnz on 2006-07-22
BTW, I got the ps (postscript) file as well, would it be better to convert that to PDF instead of resizing the PDF?

I need the dimensions in inches btw... would ImageMagick be able to do that?

---

### Post by bensibensa on 2007-10-31
thanks but size is in pixels , and the quality wasnt that great .. 
Still looking

---

### Post by Whiffle on 2007-10-31
You're going to need something like adobe acrobat to open up the file and re-create it in another size.  If it was created by LaTeX or something you could recompile it there, but I don't think you'll find any programs that can do it in one step.

---

