---
title: "converts series of images to PDF"
date: 2009-03-11
forum: General Help
---

### Post by Shady3D on 2009-03-11
i want to convert series of .png images to 1 PDF, so is there a command or a feature in a program that i can use to do this

---

### Post by ww711 on 2009-03-11
You could paste the images into a openoffice document and then print to a pdf

---

### Post by kestrel1 on 2009-03-11
The above is about right, but select to export the document as a PDF. I do this a fair bit & it works well.
BTW, I use OpenOffice 3 for this.

---

### Post by Shady3D on 2009-03-11
error was here

---

### Post by Shady3D on 2009-03-11
oh i just found the solution, using imagemagick package, i can use convert and the name of the image(s) and the last one will be the output
```

convert images_*.png all.pdf
or
convert images_01.png images_02.png images_03.png all.pdf

```

---

### Post by kestrel1 on 2009-03-11
Cool.
I am normally creating documents that need to be PDF, so if you require text in there use OO.

---

### Post by Shady3D on 2009-03-11
> **kestrel1 said:**
> Cool.
I am normally creating documents that need to be PDF, so if you require text in there use OO.
yes, but in my case i have a series of scanned images that i want in PDF, but what u say is good in case that i want to add something

---

