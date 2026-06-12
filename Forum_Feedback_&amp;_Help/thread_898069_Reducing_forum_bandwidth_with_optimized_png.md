---
title: "Reducing forum bandwidth with optimized png"
date: 2008-08-22
forum: Forum Feedback &amp; Help
---

### Post by FakeOutdoorsman on 2008-08-22
I often use [pngcrush]("http://pmt.sourceforge.net/pngcrush/"), [optipng]("http://optipng.sourceforge.net/"), and [advpng]("http://advancemame.sourceforge.net/comp-readme.html") to compress and optimize PNG files.  For example, rank_6.png, from this forum is originally 1474 bytes, but it can be reduced to 951 bytes with no change in visual quality.  ubuntulogo.png is 5443 bytes vs 2669 bytes. Attached are the optimized images.  I use the following script:
```
#!/bin/sh
# ./pngoptimze.sh input.png output.png

# Remove color profiles for IE so it renders correctly.
pngcrush -rem gAMA -rem cHRM -rem iCCP -rem sRGB $1 $2

# Reduce the size of the PNG IDAT data stream.
optipng -o7 $2

# Remove ancillary chunks, concatenate all individual IDAT chunks, then re-encode the combined PNG image file using the 7-Zip deflate method.
advpng -z -4 $2
exit
```
These programs are all available in the universe repository (advpng is part of advancecomp) and might be worth looking at for the forum.

---

### Post by Joeb454 on 2008-08-22
I didn't noticed a difference on the bean image. But the left hand curve of the Ubuntu logo is a different color :)

Though I can see why this wouldn't be a bad idea with the volume of people who visit the forums.

---

### Post by FakeOutdoorsman on 2008-08-22
Hhmm...a different color, you are correct.  My previous tests on my sites didn't change, but I will find out which particular program changed the color.

Edit: I found my mistake of missing the color change.  Mirage doesn't show a color change between the logos, but Firefox does.

---

### Post by FakeOutdoorsman on 2008-08-22
It appears that pngcrush and advpng can change the colors, but optipng alone didn't change the colors and it decreased the logo size by 48.89% to 2782 bytes.

---

