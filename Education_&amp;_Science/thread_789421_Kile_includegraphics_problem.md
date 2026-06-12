---
title: "Kile includegraphics problem"
date: 2008-05-10
forum: Education &amp; Science
---

### Post by MarshyTheKid on 2008-05-10
I am currently writing a research paper using Latex and Kile.
In my paper I have 4 jpg graphics I want inserted. I am using figure float. The first image comes out where I want it, but the others do not. They either appear a few pages down or at the end of the document in the middle of my references. I have tried changing the parameters from[htp] to H, h, ht, !h, etc, yet nothing makes it better.
Any tips or tricks I don't know about? I have it in a figure object so I can reference them.

---

### Post by dvase on 2008-05-10
The \clearpage command has helped me in the past with this issue, it forces the end of a page and places all the floats that have yet to be printed.  The disadvantage of this command is that it can abruptly change the natural document flow.

---

### Post by Lateralis on 2008-05-11
This is a fairly common issue I used to encounter, although I use encapsulated postcript (.eps) images rather than JPEG.  Primarily because .eps files seem to look a bit better, but also physics journals only want .eps images; since they're vector images and not bitmaps, they scale much more nicely and do not get grainy and pixelated.  Moreover, LaTeX is FAR happier dealing with .eps files than JPEG images.  

With .eps files, you have a bounding box which surrounds the figure.  The bounding box in the .eps file is used by LaTeX to asign space in the document.  If the bounding box is a funny size or in a funny place then the image will look funny in the document - either off to one side, squished in a corner, located at the end of the chapter on a separate page etc...  Fortunately, programmes like GhostView allow you to see where the bounding box is so you can adjust the position and size of the bounding box so it only surrounds the figure and not lots of white space.  

So, my tips and advice would be to convert everything to .eps, get Ghostgview (will need Ghostscript) and get your bounding boxes right.  You should then have no trouble with figures.

---

### Post by quasimotor on 2008-05-16
Or you could use the placeins package. You can then build barriers for all floats with \FloatBarrier.

---

### Post by Crummy_Gummy on 2008-09-02
It seems that you can't use png, jpeg etc with the latex command.
You need to use pdflatex. Its a bit annoying but something I can work around. Please let me know if I am wrong.

---

