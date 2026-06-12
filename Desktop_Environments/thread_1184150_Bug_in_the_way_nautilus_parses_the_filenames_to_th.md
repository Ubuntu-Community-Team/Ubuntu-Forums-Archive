---
title: "Bug in the way nautilus parses the filenames to thumbnail?"
date: 2009-06-10
forum: Desktop Environments
---

### Post by fh_scott on 2009-06-10
I noticed when one invokes the built in "Rotate Images..." function in Nautilus by right-clicking on a JPG(i.e. Image.JPG) the resultant file "Image.rotated.JPG" does not get thumbnailed.

As soon as the '.' between Image and rotated is removed ('Imagerotated.JPG') the thumbnail shows right up, implying nautilus is parsing the filename from left to right looking for the extension after the first period it finds, rather than from the right.

This is on 9.04.

-scott

---

### Post by asmoore82 on 2009-06-10
I assume you're using the ``nautilus-image-converter'' package -
BTW, thanks for introducing me to it!!!

I just installed it and everything works fine for me -
tested with a png and a jpg - Ubuntu 9.04 Jaunty here.

For me, there is a 1~2 second delay before the thumbnail appears though.

---

### Post by fh_scott on 2009-06-11
curious, it works as expected on my desktop (x86_64) but fails on my laptop (x86)

---

