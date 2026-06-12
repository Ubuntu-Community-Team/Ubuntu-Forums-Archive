---
title: "Copying images from pdf files"
date: 2006-06-22
forum: Desktop Environments
---

### Post by benk on 2006-06-22
Does anybody know how to copy images (or just a general selection) from pdf documents? Acrobat reader has a tool that lets you select an image (or an area) in a pdf document and supposedly copies that selection but it doesn't work (it doesn't seem to copy anything at all).

I've also tried pdftohtml which doesn't seem to do anything at all for me either. A regular "pdftohtml doument.pdf" generates html files with frames but no actual content.

This is one of the last things keeping me from deleting my windows partition.

---

### Post by aysiu on 2006-06-22
Why not just install Acrobat Reader, then, if it suits your needs? [Enable extra repositories](http://www.psychocats.net/ubuntu/sources) and ```
sudo aptitude update
sudo aptitude install acroread
```

---

### Post by wylfing on 2006-06-22
**benk** - It's hard to tell from your post whether you are having problems with Acrobat Reader, or you were using other tools that were missing features of Reader.

As was said, you can install Reader and it's capable of copying text and graphics just fine. I am pretty sure you can use ImageMagick to convert PDFs to raster images as well (e.g., TIFF or JPEG) and then you can tinker with those if that's easier.

---

### Post by benk on 2006-06-22
Hmm...I think it may actually be a problem with Gimp (or at least me not knowing how to use Gimp). What I had been trying to do is copy an image from a pdf file using Acrobat Reader's "snapshot" tool and then I was trying to paste that image into Gimp (just using Edit->Paste/Paste Into/Paste As New)...that doesn't seem to work.

I just tried pasting it into OpenOffice writer though and that does work...it pastes the image that I copied from Acrobat Reader.

Now all I have to do is find a way to get that image from writer into Gimp.

---

### Post by aysiu on 2006-06-22
You can paste it into Kolourpaint just fine.
I don't know what's going on with GIMP.

---

### Post by temcat on 2006-06-23
Benk, KOffice can extract all images from your pdf and save them sequentially numbered. (By images I mean raster images, e.g. photos, screenshots etc, that were inserted in PDF document, not vector graphics done inside PDF.) It can extract text, too, though not in a manner suitable for word processing (does not properly recognize paragraphs yet.)

---

### Post by patrick295767 on 2006-06-23
[INDENT][I]also, non native:
(I usually use adobe illustrator to get the highest result)
(wine or vmware) 

[/I][/INDENT]

---

### Post by mexlinux on 2006-06-23
That is a standard feautre in KPDF

---

### Post by Endolith on 2007-06-05
> **mexlinux said:**
> That is a standard feautre in KPDF

It doesn't seem to be.  All KPDF can do is export a selection as an image, as far as I can see.  It should be able to extract the images at their original resolution.

---

### Post by apienk01 on 2007-06-20
The xpdf package contains a nifty utility named 'pdfimages' that does just that - extracts all bitmaps from a pdf to ppm files in original resolution.

---

### Post by rajan on 2007-10-25
FYI the poppler library includes xpdf rendering, but the pdfimages that is included in this (or maybe it came from evince... i don't know, but pdfimages was installed by default via one of these sources) didn't work. I had to install the complete xpdf package and now pdfimages works flawlessly. 

As of this post, i'm using 6.06.

---

