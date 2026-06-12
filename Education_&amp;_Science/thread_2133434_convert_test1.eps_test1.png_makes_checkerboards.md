---
title: "convert test1.eps test1.png makes checkerboards"
date: 2013-04-08
forum: Education &amp; Science
---

### Post by xadder on 2013-04-08
Hi,

I have a pile of scatter plots (postscript) which are essentially black crosses and lines on an empty background. I want to use imagemagick convert command to make .png files from these, e.g.

convert test1.eps test1.png

Works great, except that the background is shown as an ugly checkerboard pattern in viewers such as geeqie. I know this pattern is a default fill, but I would prefer a simple white background for all such plots.

I tied various options in "convert" to achieve this (e.g. -transparent-color, -undercolor), but the checkerboard won't go away. (I need a command line solution, I work through 1000s of such plots each year.)

Help appreciated!

---

### Post by NanakiXIII on 2013-04-11
Try some of these suggestions:

[http://stackoverflow.com/questions/2322750/replace-transparency-in-png-images-with-white-background]("http://stackoverflow.com/questions/2322750/replace-transparency-in-png-images-with-white-background")

Apparently it also depends on whether you have imagemagick or graphicsmagick.

---

### Post by xadder on 2013-04-13
Hi NanakiXIII,

Many thanks! Using -alpha off works great. Phew!

---

