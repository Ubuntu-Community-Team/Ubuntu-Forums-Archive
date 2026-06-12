---
title: "LeX, help and problems"
date: 2008-02-28
forum: Education &amp; Science
---

### Post by Sugz on 2008-02-28
so i am trying to create professional looking documens using LateX, but have not got time to fiddle with the syntax so i found Lex.
But i cant seem to be able to us images such as .jpg and . png. 

I get this message when i try to compile and view the documents

"No information for converting png format files to eps.
 Define a converter in the preferences".

This is the same for .jpg

and when i try to open some of the ready-made templates i get the following error.. 

```
The layout file requested by this document,
docbook.layout,
is not usable. This is probably because a LaTeX
class or style file required by it is not
available. See the Customization documentation
for more information.
LyX will not be able to produce output.
```

Are there any additional packages i need in order to use Lex, without problems and also a fix to the above problems?

Thanks in advance
-Sugz

---

### Post by aJayRoo on 2008-02-29
I don't know anything about Lyx specifically but I know that latex cannot use png or jpeg images. You should use encapsulated postscript (.eps) or postscript (.ps) images. If you are using pdflatex then you will be able to use a variety of image formats with the exception of postscript and encapsulated postscript. If you need to convert images from one format to another then you can use the command line program convert. To install it you need to install imagemagick:
```
sudo apt-get install imagemagick
``` once you have that installed you can use the command:
```
convert myimagefile.jpg myimagefile.eps
``` to convert a jpeg file to eps. Convert is very useful as it can convert between most formats just using a command like the one given, just change the extensions to be appropriate for your situation. Hope that helps.

---

### Post by lad.kocb on 2008-03-03
1. might work: Convert your images to pdf as indicated below
2. always works: LyX -> export to latex -> pdflatex 

Part 1.
google search: lyx "pdf images"  includegraphics
indicates that LyX accepts pdf images.
Convert your images to pdf as indicated below (needs ImageMagick)

Part 2.
With most latex packages is also distributed
pdflatex
Pdflatex accepts (only) pdf and png images (as far as I know).
The easiest procedure is to export your document from LyX to latex
and then run pdflatex on the exported tex file, after having
converted the images .

Converting images:
To use your images in pdflatex, use the command convert 
(The convert program is a member of the ImageMagick package)
e.g.
(on command line: )
convert mypict.jpg mypict.pdf      (this is probably best choice)
or 
convert mypict.jpg mypict.png

---

### Post by lad.kocb on 2008-03-03
Using pdflatex and including eps graphics:
(specification to my previous reply)

pdflatex does not use eps, only pdf
The best and most efficient conversion is

epstopdf mydrawing.eps

the command makes mydrawing.pdf

(The pdf file will be allways smaller than the eps file)

Some latex packages contain epstopdf.sty or similar, which
attempts the conversion  epstopdf  automatically - but 
this depends on the latex version and I met it sometimes broken.

the mentioned ImageMagick's convert can also do this converion, 
but it does not allways work properly (I met boundingbox problems)

---

### Post by GregC666 on 2008-03-24
I had the same problem and it went away as soon as I installed the imagemagick package, with no further manual Lyx configuration. Jpeg, bmp, png are all automatically converted for me.

---

