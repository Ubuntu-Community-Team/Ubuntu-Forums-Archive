---
title: "Getting EPS with embedded TeX converted to PNG"
date: 2010-09-02
forum: Education &amp; Science
---

### Post by jabalsad on 2010-09-02
Hi all,

I'm using LyX as a TeX editor and I'm using Metapost to draw images for my documents. Metaposts supports embedding TeX inside the graphic, and after generation I get an EPS file. In order for these images to be displayed correctly in LyX, I need a converter that can correctly convert these EPS files to PNG. I think this task is trivial when the EPS files does not contain TeX, but otherwise all the converters I try spews errors. Can anyone tell me of a command line util that will do so?

---

### Post by Azrael3000 on 2010-09-03
did you try gimp or inkscape yet?

---

### Post by xadder on 2010-09-03
It would help if you said which converters you have tried. Did you try for example, "convert file.eps file.png"?

---

### Post by FreeTheBee on 2010-09-03
I don't use lyx but with pdflatex I use epstopdf to convert eps images on the fly to pdf. For graphs I prefer to keep vector images over conversion to png.

---

### Post by Azrael3000 on 2010-09-04
I reread the first post. And I would agree with FreeTheBee, convert to pdf via epstopdf and then use these images in your tex files. I don't work with Lyx either, but normally it should work just fine.

---

