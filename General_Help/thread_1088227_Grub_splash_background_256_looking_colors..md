---
title: "Grub splash background 256 looking colors."
date: 2009-03-05
forum: General Help
---

### Post by dragos240 on 2009-03-05
Okay so i decided i wanted the gusty default background on my grub, so i used QGRUBEditor to do it, it came out, but it was in 256 colour and grub only displayed a portion of the image, not the entire one, can anyone help me at least get it to 16 bit or posibly 32 bit?

---

### Post by jlochhead on 2009-03-05
Image > Mode > Indexed in GIMP.

---

### Post by dragos240 on 2009-03-05
> **jlochhead said:**
> Image > Mode > Indexed in GIMP.

No it's not the image, thats in 16 bit format, grub doesn't display it right...

---

### Post by dragos240 on 2009-03-06
Bump!

---

### Post by dragos240 on 2009-03-08
Bump!

---

### Post by warp99 on 2009-03-08
Grub doesn't do 256 colors, only 14/15 colors unless your using version 2:

[http://wiki.debian.org/Grub/SplashImage](http://wiki.debian.org/Grub/SplashImage)

---

### Post by dragos240 on 2009-03-08
> **warp99 said:**
> Grub doesn't do 256 colors, only 14/15 colors unless your using version 2:

[http://wiki.debian.org/Grub/SplashImage](http://wiki.debian.org/Grub/SplashImage)

How do i upgrade to version 2?

---

### Post by warp99 on 2009-03-08
You don't need to upgrade. Just "dither" you picture down to 14 colors or 15 colors if the background is black by using gimp and index mode. The image needs to have a resolution of 640x480 and be saved as an .xpm file. This was explained in the previous link I posted.

Upgrading to version 2 is too involved of an option with either Hardy or Intrepid, but it will be included in Jaunty coming out next month.

---

### Post by dragos240 on 2009-03-08
> **warp99 said:**
> You don't need to upgrade. Just "dither" you picture down to 14 colors or 15 colors if the background is black by using gimp and index mode. The image needs to have a resolution of 640x480 and be saved as an .xpm file. This was explained in the previous link I posted.

Upgrading to version 2 is too involved of an option with either Hardy or Intrepid, but it will be included in Jaunty coming out next month.

Oh i see.... i upgraded via synaptic package manager anyway.

---

### Post by warp99 on 2009-03-08
> **dragos240 said:**
> Oh i see.... i upgraded via synaptic package manager anyway.

You got lucky since a few people have been getting burned upgrading. That's why the grub2 packages are not included in the main repositories, but instead are in universe.

---

