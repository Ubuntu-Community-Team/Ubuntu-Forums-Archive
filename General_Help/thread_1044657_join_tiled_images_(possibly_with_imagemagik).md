---
title: "join tiled images (possibly with imagemagik)"
date: 2009-01-19
forum: General Help
---

### Post by lavinog on 2009-01-19
I have a group of pngs that are part of a 6x6 html table. It is an image formated for an Ipod, but I want to use it on a different device that can handle large images.
Each image is 320x240, and is labeled 1-36
They are aranged:
1 2 3 4 5 6 
7 8 9 10 11 12
..
31 32 33 34 35 36

How can I merge them all into one png?
I suspect imagemagick:convert should be able to do it, but I only understand the basic uses of it.
A command line method is preferred because I will have to do this to a number of images.

---

### Post by lavinog on 2009-01-19
It looks like montage is the command I need to use

---

### Post by mikelygee on 2009-01-19
'montage' from ImageMagick should do the trick. Based on the examples at 
[http://www.imagemagick.org/Usage/montage/]("http://www.imagemagick.org/Usage/montage/"), I'd try something like this:
[INDENT][FONT="Courier New"]montage image[0-9]*.png  -tile 6x6  -geometry 320x240+1+1  unified_image.png
[/FONT][/INDENT]

---

