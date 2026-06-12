---
title: "How to resize icons in the panel"
date: 2007-08-08
forum: Desktop Environments
---

### Post by ANTON_AL on 2007-08-08
Hi all !!

I can resize icons at the Desktop. But how to resize icons in the standart Ubuntu panel? 
If i resize the panel, icons will be biger, but the size of icons is limited ~ 40 pixels.
How can i make icons bigger ??

---

### Post by be4truth on 2007-08-09
Why is it limited to 40 pixel. I can have icons up to 120 pixel on the panels. Which Ubuntu are you using?

---

### Post by ComplexNumber on 2007-08-09
> **ANTON_AL said:**
> Hi all !!

I can resize icons at the Desktop. But how to resize icons in the standart Ubuntu panel? 
If i resize the panel, icons will be biger, but the size of icons is limited ~ 40 pixels.
How can i make icons bigger ??
what icon theme are you using?

---

### Post by ANTON_AL on 2007-08-10
I use Ubuntu 7.04. Icon theme - Leopard ( [http://www.gnome-look.org/content/show.php/Leopard+look?content=60349](http://www.gnome-look.org/content/show.php/Leopard+look?content=60349) )
I have tested another themes, and i get the same result: panel can be big up to 120 pixels, but icons are small. However, icon-files are .png 128x128 and bigger.

---

### Post by ComplexNumber on 2007-08-10
> **ANTON_AL said:**
> I use Ubuntu 7.04. Icon theme - Leopard ( [http://www.gnome-look.org/content/show.php/Leopard+look?content=60349](http://www.gnome-look.org/content/show.php/Leopard+look?content=60349) )
I have tested another themes, and i get the same result: panel can be big up to 120 pixels, but icons are small. However, icon-files are .png 128x128 and bigger.
it's got nothing to do with the gtk theme. if you have a look at the Human icon theme, not all of the icons are either scalable or 128x128. some only exist in (say) 32x32, so that's as big as they get. some icons only exist in 48x48, and that's as big as they get. etc.
if there is an icon on your panel that isn't in the Human theme, it will use the icon from gnome or hicolour theme instead. and the same applies - if the icon only exists as 32x32, that's as big as it will ever get.

---

