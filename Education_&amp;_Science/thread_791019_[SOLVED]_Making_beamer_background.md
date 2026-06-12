---
title: "[SOLVED] Making beamer background"
date: 2008-05-11
forum: Education &amp; Science
---

### Post by amyst on 2008-05-11
I want to use a svg or jpg file as background for creating pdf presentation slides using beamer. I can't tell if this can be done based on online documentations. Can someone point me to the right direction? Thanks!

---

### Post by ppm on 2008-05-12
Unfortunately, I don't know how to setup the background, but at least you can use beamer with jpg images. pdflatex is needed to compile.

---

### Post by amar on 2008-05-12
have you tried the solution at [tug.org/mail-archives/texhax/2007-March/008035.html]("http://tug.org/mail-archives/texhax/2007-March/008035.html")

```
\usebackgroundtemplate{\includegraphics[width=\paperwidth]{<your_fig>}}
```

---

### Post by amyst on 2008-05-12
Thanks amar. I got it working with png files.

---

