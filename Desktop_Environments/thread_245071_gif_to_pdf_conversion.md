---
title: "gif to pdf conversion"
date: 2006-08-27
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-08-27
I'm looking for a way to connvert multiple gif files to one pdf file.

I found out that one way would be printing to ps and the use ps2pdf.

However, I was unable to find out how to print multiple gif files to one ps file.

Does anyone know / have a better idea?

Thanks

Gabriel

---

### Post by aysiu on 2006-08-27
Let's say your GIF files are in a folder called /home/gabrielwolff/Desktop/images.

```
sudo aptitude update && sudo aptitude install imagemagick pdfjam
cd ~/Desktop/images
mogrify -format pdf *.gif
pdfjoin *.pdf
```

---

### Post by GabrielWolff on 2006-08-27
Wow thanks good great fantastic

1) Is there a possibility to join only a few of all files in a certain folder?
2) What if I want to resize all pages to the same size? Possible?
3) Is it possible to create bigger and smaller pdf-files? Maybe that's the same question as 2)...
4) How about the name of the pdf file? Can I edit it only after creating the file?

Thanks

Gabriel

---

### Post by aysiu on 2006-08-27
1. If you list the files one by one.

2. I don't know. Check out this page for more options:
[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php)

4. You can specify the name of the output file: ```
pdfjoin *.pdf --outfile *newname*.pdf
```

---

