---
title: "PDF creator?"
date: 2008-09-28
forum: Education &amp; Science
---

### Post by KOTAPAKA on 2008-09-28
Heya I have a Adobe Acrobat Pro on Windows. Since I no longer use windows and currently I had to scan some files I ended up looking for a program that can create pdfs from images in linux. Now I now Xsane has the option of creating a pdf but I'd rather use a program as it has more options, usually. Can anyone suggest such a program?

---

### Post by brunovecchi on 2008-09-28
With Gimp, you can save your images as a postscript file (.ps). Then you can convert them to pdf with the command
```
ps2pdf image.ps
```
It will output image.pdf in the working directory.

As of the options, I don't know exactly what you mean, but I'm pretty sure that you can edit your image to your liking with Gimp before saving it as pdf.

Hope it helps!

---

### Post by DrOlaf on 2008-09-28
Inkscape will also save as PDF. I used that recently to load some old PDFs, edit them a little, and save them as PDF.

---

### Post by rsambuca on 2008-09-28
scribus is another alternative.

---

### Post by Xnst on 2008-09-29
I think convert, a part of ImageMagic, can do that.

```
convert image.jpg image.pdf
```

I guess you have loads of options as well.

---

### Post by nikogawa on 2008-09-29
Maybe gscan2pdf is an option

---

### Post by fsando on 2008-10-02
> **KOTAPAKA said:**
> Heya I have a Adobe Acrobat Pro on Windows. Since I no longer use windows and currently I had to scan some files I ended up looking for a program that can create pdfs from images in linux. Now I now Xsane has the option of creating a pdf but I'd rather use a program as it has more options, usually. Can anyone suggest such a program?

I do that all the time.

As for convenient programs for pdf in Linux we'll probably have to wait a little longer (I believe a lot of work is being done in that area but it just isn't ready yet)

I use kooka for scanning but I guess sane is just as good (had some trouble with it initially, tried kooka and stayed there). Then I use imagemagick to treat the scanned images and finally I stitch them together with pdftk.

As I write this I realize how geeky this approach is so it may not suit your needs but anyway it works great.

I've made a script that assumes you have a series of double page scans, scanned to bmp-files. They are first split into individual pages and then put together in a full pdf document. It's well documented otherwise I wouldn't remember myself what it's doing.

---

