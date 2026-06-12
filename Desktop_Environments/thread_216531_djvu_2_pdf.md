---
title: "djvu 2 pdf????"
date: 2006-07-15
forum: Desktop Environments
---

### Post by orlox on 2006-07-15
is there any app to create a pdf file from a djvu file??

---

### Post by Nonno Bassotto on 2006-10-14
You can install djvulibre-bin from the repos and then use djvups to convert to ps and finally ps2pdf to convert in pdf. Don't know a direct way.

---

### Post by Halca on 2007-08-17
Hey! I specifically registered on these forums just so i could tell you how to do it:

1) Install djvulibre and djvu tools (djvu.sourceforge.net/ or sudo apt-get install djvulibre)
2) Once you've done that, check you've got ddjvu, and then move into the directory your (crappy) djvu file is in.
3) Follow the below directions:

[PHP]
ddjvu -format=tiff yourfile.djvu yourfile.tiff 
tiff2pdf -o yourfile.tiff yourfile.pdf
[/PHP]

There, you've got a PDF. If you need to dump the text from the DJVU -- check the man page for djvu (man djvu)

ENJOY!

---

### Post by alexeyten on 2007-08-30
to get tiff2pdf you should install libtiff-tools
```
sudo apt-get install libtiff-tools
```
And I recommend to use -j switch to get smaller output file.
```
tiff2pdf -j -o outfile.pdf yourfile.tiff
```

---

### Post by harakiri1976 on 2007-11-14
Hello Guys!

I made something different. I Converted first to [COLOR="Red"].ps[/COLOR] and after to [COLOR="Red"].pdf[/COLOR]. I used [COLOR="Red"]djvups[/COLOR] to convert to [COLOR="Red"].ps[/COLOR] and [COLOR="Red"]ps2pdf[/COLOR] to convert to [COLOR="Red"].pdf[/COLOR]. These were the steps:

[COLOR="Blue"]1 -  djvups filename.djvu filename.ps
2 - ps2pdf filename.ps filename.pdf[/COLOR]


It is simple! However, the 1st step turn the previous file too long! I had [COLOR="Red"]5.5MB djvu[/COLOR] file and got a [COLOR="Red"]1.5GB ps file[/COLOR]!!!That's right! 1.5 GIGABYTES! But, then with 2nd step ([COLOR="Red"]ps2pdf[/COLOR]) the file went smaller but about 9 times bigger than the original one. I mean, I got a [COLOR="Red"]49.8MB PDF File[/COLOR]. Anyway, it's understandable. It's a book with 178 pages composed mainly with pics.

Hope this help as you all helped me with this post.

Thank You!

---

### Post by spearo on 2008-01-03
sweet the converting to a ps then to pdf wrked brilliantly. takes a while though because like stated above, when turned to a ps, the file size increases ALOT

---

### Post by ah_mad on 2008-01-10
There is another benefit of using ddjvu instead of djvups. If your djvu file is in "Landscape" view djvups changes it to portrait view by default which is undesirable!

Bests,
Ahmad

---

### Post by myle on 2008-03-31
Is there any other way? The first one didn't work for me

```
ddjvu -format=tiff source.djvu yourfile.tiff 
*** glibc detected *** ddjvu: double free or corruption (fasttop): 0x08865c90 ***
======= Backtrace: =========
....
....
Aborted (core dumped)

```

and the second one produces a huge file and I don't want to use it.

---

### Post by dspdude on 2008-05-13
The whole forum has this backwards. The goal is to make a DJVU file FROM a PDF.

I found a useful link here: [http://www.howtoforge.com/creating_djvu_documents_on_linux](http://www.howtoforge.com/creating_djvu_documents_on_linux)

I'd feel bad just copying and pasting there solution to this forum, but I'll summarize it.

You convert the individual pages in the PDF to PBM files using  "pdftoppm", then convert it to Djvu bi-tonal using "cjb2", and then link them together with "djvm"

---

### Post by Sordelka on 2008-05-31
> **ah_mad said:**
> There is another benefit of using ddjvu instead of djvups. If your djvu file is in "Landscape" view djvups changes it to portrait view by default which is undesirable!

Bests,
Ahmad

Yea, but it is impossible to convert multipage documents into tiff with this tool...

---

