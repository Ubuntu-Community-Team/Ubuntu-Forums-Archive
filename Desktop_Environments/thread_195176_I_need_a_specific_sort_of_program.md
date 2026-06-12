---
title: "I need a specific sort of program"
date: 2006-06-12
forum: Desktop Environments
---

### Post by snellgrove on 2006-06-12
Hi all,

I am not sure if this is the correct forum, exactly but anyways - hopefully this will not be too complicated.

Basically, I am using Hugin to create panorama's which is fun, except I only have 1GB RAM & stupidly a 1.4GB swap partition - so when I try to stitch 10+ images together, I run out of both and have to kill hugin.

So I want to resize my images, so I can create these pictures..  but it has to be in batch mode, because I dont want to resize each one individually (I might as well use GIMP if thats the case) 

but the complication comes in, because I need to keep the EXIF data for Hugin - I have tried several resizers from sourceforge, but can't find one that does:

batch, keeps the exif, and resizes.

anyone know of any programs that do this? :KS

---

### Post by aysiu on 2006-06-12
How about ImageMagick (which is installed by default)?

[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php)

---

### Post by snellgrove on 2006-06-12
Excellent, I'll give that a go. I installed Image Magick from Synaptic, but couldn't run it in the terminal with 'imagemagick' or find it in the Graphics menu's :p

'Installed files' in the properties, in synaptic said it had a load of things like convert etc but I didn't really know how to use it, or which one was which.

I'll give 'mogrify' a go, hopefully it saves EXIF by default :)

Thanks for the help

---

### Post by snellgrove on 2006-06-12
[QUOTE=snellgrove]Excellent, I'll give that a go. I installed Image Magick from Synaptic, but couldn't run it in the terminal with 'imagemagick' or find it in the Graphics menu's :p

'Installed files' in the properties, in synaptic said it had a load of things like convert etc but I didn't really know how to use it, or which one was which.

I'll give 'mogrify' a go, hopefully it saves EXIF by default :)

Thanks for the help[/QUOTE]

:edit:

thats brilliant, just running it now on 98 photos! would have been a real pain using GIMP for that, as great as it is!

---

