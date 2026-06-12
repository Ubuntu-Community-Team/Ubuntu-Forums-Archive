---
title: "Edgy Aiglx: screensaver as desktop wallpaper"
date: 2007-01-02
forum: Desktop Environments
---

### Post by Attila_fdd on 2007-01-02
I decided to install the edgy eft and all works good in my nb. But with aiglx i cannot use xwinwrap to have a screensaver as desktop wallpaper (i used dss script with xwinwrap before).
Is there any package for aiglx to do that?

---

### Post by Attila_fdd on 2007-01-03
up

---

### Post by Attila_fdd on 2007-01-04
up

---

### Post by Rever75 on 2007-01-05
I have it working using xwinwrap cvs from this repo.... 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

Warning using this repo will also give you svn Beryl so use at your own risk.

---

### Post by Attila_fdd on 2007-01-06
yes i tried that, but there is a problem. When i ran that my old desktop was hidden from a black one with the screensaver running. If i rotate the cube i can see the old wallpaper from inside and the cube doesnt become transparent anymore (in the 4 desktop sides).

How can i make it works correctly?

I also tried reducing the opacity of the screensaver but my desktop was darker and the screensaver was less visible

---

### Post by Rever75 on 2007-01-06
I believe if I remember right screensavers run from a black background to begin with. So when using xwinwrap to make a screensaver a desktop, it will use a black background. Also remember you are not actually replacing nautilus in favor of xwinwrap as your desktop screen draw. This program runs on top of your desktop making it appear to be your desktop. So when you run a screensaver with out opacity your cube is transparent you just cannot see through the 4 sides since xwinwrap is not transparent. If you set xwinwrap to be a percent transparent you will see through it to you actual Desktop drawn by nautilus. In short there is not real program that replaces your desktop drawing. Nautilus is still drawing the desktop behind xwinwrap. I hope this makes sense I tend to explain better in words not writing.

---

### Post by Attila_fdd on 2007-01-06
i can unterstand what you said but before, with dapper and xgl, xwinwrap works good and withtout  opacity i can see my desktop behind the screensaver. why?

---

### Post by mexlinux on 2007-01-23
> **Rever75 said:**
> I have it working using xwinwrap cvs from this repo.... 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

Warning using this repo will also give you svn Beryl so use at your own risk.

What command are you using?

---

