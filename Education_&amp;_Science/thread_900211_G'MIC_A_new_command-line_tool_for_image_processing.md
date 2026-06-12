---
title: "G'MIC: A new command-line tool for image processing"
date: 2008-08-25
forum: Education &amp; Science
---

### Post by dtschump on 2008-08-25
Hi everyone,
I would like to say a word about **G'MIC**, a new open-source tool for image processing and manipulation, located at *[http://gmic.sourceforge.net/]("http://gmic.sourceforge.net")*
There is available binaries already for Ubuntu Hardy users, but unfortunately no available .deb packages yet (if anyone is experienced enough to make it quickly, and has more free time than I have, do not hesitate to contact me, this should be a quite simple package to do).

**G'MIC** is a console-based image processing tool whose goal is to convert, manipulate and visualize generic **1D/2D/3D multi-spectral image** datasets. This includes classical *color images*, but also more complex data as **image sequences** or **3D volumetric images**. It has been designed with portability in mind, and thus runs on a wide variety of different platforms.

**G'MIC** has a lot of options to convert and process image files, like any other existing image converter (*ImageMagick* or  *GraphicsMagick* for instance). Anyway, there are specific features  to **G'MIC** which make it particular and interesting :

[LIST]
[*]It can process a **wide variety** of images, including multi-spectral images (with less or more than 3 channels), 3D volumetric images and video sequences.
[*]It considers that image pixels are **typed**, so it can work with images coded with 8bits or 16bits integers per channel, as well as float-valued images. Reading and writing complex image types is then easy.
[*]It provides a simple but efficient **image visualization** and exploration module both for 2D or 3D images.
[*]It has an embedded 3D engine, and can read/write a 3D vector object and visualize it. Moreover, it can **extract 3D informations** from images (elevation map, isophotes or isosurfaces).
[*]It allows to create user-defined macros that can define **custom commands**. So, basically, **G'MIC** can be used to design your own filters easily, by combining 'atomic' image processing operations together.
[/LIST]

Just to illustrate (here for 2D color images only), I copy/paste some examples from the web site :

Cartoon example : (use custom user-defined macro)
```
gmic -m macros.gmic input.jpg -cartoon
```
[IMG]http://gmic.sourceforge.net/img/sample12.jpg[/IMG]

Wave example : (use custom user-defined macros) 
```
gmic -m macros.gmic sample.jpg -tile2x2 -wave -o sample11.jpg
```
[IMG]http://gmic.sourceforge.net/img/sample11.jpg[/IMG]

Another example to show how the commands are working :
```
gmic sample.jpg -smooth 30,0,1 -flood 58,134,0,50,10000,8000,4000 -flood 110,63,0,30,20000,20000,0 [0] -plasma[0] -n 0,255 -+ -equalize -n 0,255 -o sample7.jpg
```
[IMG]http://gmic.sourceforge.net/img/sample7.jpg[/IMG]

Look at the site for other interesting examples.

**G'MIC** is based on the [CImg Library]("http://cimg.sourceforge.net") (a C++ template image processing library). Thus it offers lot of CImg capabilities, without having to code a single C++ line.

I hope you will this post interesting, or at least informative.:KS

D. Tschumperlé.

---

### Post by rye_ on 2008-08-25
That's really great!!

---

