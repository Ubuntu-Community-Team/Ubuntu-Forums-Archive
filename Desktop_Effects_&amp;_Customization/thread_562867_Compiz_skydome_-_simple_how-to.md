---
title: "Compiz skydome - simple how-to"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by Linicks on 2007-09-29
Hi all,

After reading up on this, it is very wayward on what you should do to get an image to use as a skydome.

Here is how.

Install the imagemagick package.  Next, cd to the directory of where the image is located.

If the image is **not** a *.png, we need to convert the format - if it already is, then we just need to resize with no aspect ratio to 2048x512.

All the following work in a console!

Example 1.

test.gif.

> convert test.gif -resize 2048x512! test.png

Example 2.

test.jpg

> convert test.jpg -resize 2048x512! test.png

Example 3.

test.png

> convert test.png -resize 2048x512! test1.png

etc.


The 'convert' options are obviously convert from image.format -> image.png.  -resize nnnxnnn! tells it to resize but ignore (!) aspect ration (i.e. it gets forced to the size and distorted).

If you look at the image in a viewer (gimp, display etc.) it will look all stretched and horrid - but in compiz skydome mode, it renders perfectly.


Here are some (ala Blue Peter style) I prepared earlier:

[http://www.nick.ukfsn.org/skydome/](http://www.nick.ukfsn.org/skydome/)

Nick :)

---

### Post by nikoPSK on 2007-10-13
Thanks alot! Im using compiz in gutsy and I would like to know how to get (Ive seen this before.) it to look like you're moving around the cube. Instead of you moving it.:KS

---

