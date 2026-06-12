---
title: "Trouble with ImageMagick"
date: 2006-03-07
forum: Desktop Environments
---

### Post by Itami on 2006-03-07
I've been playing with ImageMagick for making batch thumbnailing scripts and such and it works fine.  

But I keep getting errors when I try to use .jpg and .png files(gifs work without complaint).  I checked my package manager and I appear to have the .png and .jpg libraries installed.  And pngs/jpgs work just fine with other programs.

But when I do stuff like:
convert rose.png -scale 100x100 rosethumb.png

It throws this:
convert: no decode delegate for this image format `rose.png'.
convert: missing an image filename `rosethumb.png'.

Any ideas?

Edit: Ah dammit I meant to post this in the 5.10 desktop support forum.

---

