---
title: "Open Source Linux Based Chemistry Programs"
date: 2006-10-05
forum: Education &amp; Science
---

### Post by Pyr3 on 2006-10-05
I've been using Linux now for about two years, mainly just for fun and to SSH into a server farm to run Gaussian.

I'm curious as to what freely availabile chemistry programs people are using - specifically NMR processing, structure drawing (ChemTool/EasyChem sucks, imo), and perhaps just a few other ones the come in handy.  (Obviously, I've got Kalzium installed -- it rocks like The Who)

---

### Post by LaserJock on 2006-10-05
Hi Pyr3!
  BKChem is a nice molecular drawing app. It isn't in dapper but it is pretty easy to install. Ghemical is great for 3d molecular modeling and does molecular mechanics, semi-empirical, and ab initio. Fityk might help with the NMR stuff. GaussSum is a Gaussian data viewer that you can use to look at some of the data hidden in those gigantic output files ;-)

-LaserJock

P.S. If you find any good chemistry apps that aren't in the Ubuntu repos and are free/open-source, let me know.

---

### Post by alibobar on 2006-12-07
I've been trying BKChem for now, it's ok except I can't draw half and full-pointed arrows that resemble electron-transfers. I'd just like a bented arrow that can be locked to different atoms and reshapes according to the placement of those atoms.

---

### Post by neoflight on 2006-12-09
[_Raster3D_]("http://skuld.bmsc.washington.edu/raster3d/raster3d.html") seems good. and the site contains some useful links too...

[_here_]("http://en.wikipedia.org/wiki/Ray_tracing") is another source ...

---

### Post by lbyrd33 on 2007-02-13
For viewing processed nmr data you can use sparky which is an easy install. For processing and viewing you can ask to get nmrPipe and nmrDraw for free which are really powerful tools. I think nmrDraw will handle even 1-3D files while sparky is only for 2-3D.

---

### Post by jeecol on 2007-02-20
1. xdrawchem can predict NMR (1H, 13C), IR and pKa, but I never used these functions. please see [http://xdrawchem.sourceforge.net/](http://xdrawchem.sourceforge.net/)


The default setting of double bond is not good, too narrow. You can 

Format > Draw settings > double bond space --> 10 pixels.

diagram can be exported as png, svg, eps, and bmp. But when I inserted the chemical diagrams into OOo, the graphic quality was not good. 

2. So far, the best quality I have got is from chemtool and EMF file  


3. I have trouble in using bkchem. The pure structures were OK when I pasted them into OOo. But text in chemtool like CH3OH became a big,  black block in OOo. Then I knew I needed to set the frame line invisible.  

Drawings in bkchem can be exported as svg, png, pdf and sxd for OOo Draw. If I can solve the big black block in bkchem, I would like to use it instead of chemtool and xdrawchem.

By the way, maybe you can try pymol, it is fancy!
-------------------
jeecol = one dollar

---

### Post by briansvgs on 2007-05-14
Hello,

I am doing senior project for my physics class. In this project, I am studying the absorption spectrums of different elements. To do this, I am using a colorimeter to examine several solutions containing compounds dissolved in water. This colorimeter allows me to chose the wavelength and tells me the transmittance for the solution. Can someone please help me find a program that will take these wavelengths and their percent transmittance and turn them into an image that I can then add to my lab report? I am looking for something that will generate images like either this:[http://mcdb.colorado.edu/courses/3280/images/photoreception/four-spectra.gif](http://mcdb.colorado.edu/courses/3280/images/photoreception/four-spectra.gif), or this:[http://csep10.phys.utk.edu/astr162/lect/light/spectra.gif](http://csep10.phys.utk.edu/astr162/lect/light/spectra.gif).

Thanks

---

### Post by jeecol on 2007-05-21
The new version of Bkchem  (0.12 pre2, supports PC, MAC, and Linux) solves some problems in old version and it becomes my first choice in drawing chemical structure. 

For basic drawings, I highly recommend Bkchem.  

---------
jeecol  = one dollar

---

### Post by briansvgs on 2007-05-26
I submitted the project Friday. Advice would still be useful for the future, and probably others, though. Thanks.

---

### Post by daftbeaker on 2009-01-16
Quick spot of thread necromancy.

EDIT - Solved my previous problem by stopping being an idiot.  BKChem is the package I like most at the moment but it looks a bit jagged.  Is there a way to smooth out bonds and reduce the pixelation?

Also, this is probably asking a bit much but is there a way to generate structures from names and vice-versa, similar to ChemDraw?

daftbeaker

---

### Post by anglican on 2010-03-30
[B]NMR processing on Ubuntu
[/B]
Because it's written for the .NET framework you can use Kirk Marat's excellent SpinWorks program for 1D and 2D NMR processing. You'll need to install mono (available in the Ubuntu repository) then get the mono version from:

[ftp://davinci.chem.umanitoba.ca/pub/marat/SpinWorks/test_versions/](ftp://davinci.chem.umanitoba.ca/pub/marat/SpinWorks/test_versions/)

Run with "mono SW_317_mono_MDbuild.exe"

H

---

