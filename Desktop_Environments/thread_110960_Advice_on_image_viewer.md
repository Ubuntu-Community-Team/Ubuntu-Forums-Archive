---
title: "Advice on image viewer"
date: 2006-01-01
forum: Desktop Environments
---

### Post by rklauco on 2006-01-01
Hello everyone.
I am searching for image viewer.
I need following finctions:
- ability to move to next/previous picture in directory
- run fullscreen/in window
- show thumbnails of images in current folder
- rotate using lossless transformation and directly save the image

Basicly, I am searching for replacement of IrfanView from Windows.
gThumb was my choice until I found that it can't rotate the image by lossless transformation.
I tried feh, gliv, gthumb, gtksee, qiv and none of them was able to fit all my needs.

Any suggestions?
Thanks in advance.

---

### Post by MartinG on 2006-01-01
Have you tried gwenview (the standard KDE viewer)?

---

### Post by art on 2006-01-01
Maybe gqview?

---

### Post by rklauco on 2006-01-01
Yes, Gqview was THE one I was searching for.
Thanks for the tip.

---

### Post by az on 2006-01-01
[QUOTE=rklauco]Yes, Gqview was THE one I was searching for.
Thanks for the tip.[/QUOTE]

AFAIK, you need to install the jpeg-progs package 
[http://packages.ubuntu.com/breezy/graphics/libjpeg-progs](http://packages.ubuntu.com/breezy/graphics/libjpeg-progs)
to be able to manipulate jpegs (rotate and so forth) in gqview.  It is a recommended package, but not a dependancy.

I heard the new default gnome image viewer in Dapper is more like gqview in functionality and speed.

---

### Post by rklauco on 2006-01-01
Yes, I did, I found it on some other forum, tested and it worked :-)
Thanks again.

---

