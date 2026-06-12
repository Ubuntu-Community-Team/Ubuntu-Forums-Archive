---
title: "converting svg and svgz files to png en mass"
date: 2009-03-13
forum: General Help
---

### Post by Jameshardy88 on 2009-03-13
I wish to convert lots of svg and svgz (not sure exactly what these are really and how they are different from svg's but anyway) files into png, i tried using phatch and it seemed to work fine for lots of file types however svg's did not seem to be among the files that it can convert to or from, am i just missing something? if not can somebody recommend another gui method of converting them as i am not yet proficient enough to use the command line (unless VERY basic).

---

### Post by blackened on 2009-03-13
SVGZ are just SVG files that have been compressed with gzip.

You're probably not going to find anything that can do batch processing of SVG, unless you're willing to write some script for the GIMP using static sizes for conversion.

Imagemagick reputedly has support for SVG, but I don't know how good it is, and it is commandline-only.

---

### Post by viljun on 2009-03-13
on command line:

sudo aptitude install imagemagick
mogrify -format png *.svg

---

