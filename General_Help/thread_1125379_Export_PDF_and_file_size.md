---
title: "Export PDF and file size"
date: 2009-04-14
forum: General Help
---

### Post by nixi on 2009-04-14
Hello!

I use Open Office Writer to export a simple page to PDF, but the PDF is nearly 400K. Last summer I was able to export it to 12K. What happened? 

Changing JPEG-compression, or resolution, does not seem to make much of a difference regarding the file size, yet a bitmap (a low resolution black and white logo) does change appearance according to degree of compression. 

Anyone here recognize this, or know of a solution? 400K is intolerable!

---

### Post by DeMus on 2009-04-14
> **nixi said:**
> Hello!

I use Open Office Writer to export a simple page to PDF, but the PDF is nearly 400K. Last summer I was able to export it to 12K. What happened? 

Changing JPEG-compression, or resolution, does not seem to make much of a difference regarding the file size, yet a bitmap (a low resolution black and white logo) does change appearance according to degree of compression. 

Anyone here recognize this, or know of a solution? 400K is intolerable!

I just copied the text you wrote here and copied it several times into Writer until I had 1 A4 page full.(see pdf) The PDF is 18.1KB.
My settings for exporting a PDF are like the other attachments.
Maybe you changed something without knowing it.
See next posting for the last png file. A Maximum of 5 is allowed.

---

### Post by DeMus on 2009-04-14
> **nixi said:**
> Hello!

I use Open Office Writer to export a simple page to PDF, but the PDF is nearly 400K. Last summer I was able to export it to 12K. What happened? 

Changing JPEG-compression, or resolution, does not seem to make much of a difference regarding the file size, yet a bitmap (a low resolution black and white logo) does change appearance according to degree of compression. 

Anyone here recognize this, or know of a solution? 400K is intolerable!

See posting above. Here you find the last png file.

---

### Post by nixi on 2009-04-14
Thanks for your reply! 

Now I have made a similar test: plain text on a page, and the exported PDF is 27K, which seems to be in the same range as your 18K. Therefore one may suspect something in that original page as a probable cause for the increased file size. But what? 

I ditched the bitmap logo, but the exported file size decreased merely from 388K to 383K. The page also has some tables and cells (with math functions). Could they cause such increase in the file size? They didn't last summer, and I need them. Last thing I did was to delete all text, and the exported PDF is now down to 100K. That is a major difference. 

So perhaps a major part of this problem is the font I use? It is ordinary Times.

The attached file is my .odt-file: I deleted all text and the logo, but with the tables and a couple of frames it still exports to 200K (and of course there should be text and a logo in it as well).

---

### Post by DeMus on 2009-04-14
> **nixi said:**
> Thanks for your reply! 

Now I have made a similar test: plain text on a page, and the exported PDF is 27K, which seems to be in the same range as your 18K. Therefore one may suspect something in that original page as a probable cause for the increased file size. But what? 

I ditched the bitmap logo, but the exported file size decreased merely from 388K to 383K. The page also has some tables and cells (with math functions). Could they cause such increase in the file size? They didn't last summer, and I need them. Last thing I did was to delete all text, and the exported PDF is now down to 100K. That is a major difference. 

So perhaps a major part of this problem is the font I use? It is ordinary Times.

The attached file is my .odt-file: I deleted all text and the logo, but with the tables and a couple of frames it still exports to 200K (and of course there should be text and a logo in it as well).

Your 10.4KB ODT file exports as a 220KB pdf file here with my basic settings. Twice the size you have. Odd.
So yes, I do think something is a bit strange in your text file. The PDF is way too big. On the other hand, is that a big concern?
As long as all is exported and nicely visible.

---

### Post by nixi on 2009-04-14
Hi again. 

That .odt file includes a couple of horisontal rectangles I forgot to delete. That's why it exports to around 200K. Without them it is around 100K. 

That is still a lot for an empty looking page.

---

### Post by nixi on 2009-04-14
Ok, I found a solution: 

1. install a virtual printer:
```
sudo apt-get install cups-pdf
```
2. make sure there is a directory named "PDF" (/home/yourusername/PDF). That's where you will find the files. 

3. Now it should be possible to select "PDF" (listed like an ordinary printer) from the program's print menu. 

For example, that .odt file printed to 30K, way better than 400K! :)

---

