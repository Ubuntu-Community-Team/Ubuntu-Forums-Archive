---
title: "how to deal with .ecw files?"
date: 2010-02-03
forum: Education &amp; Science
---

### Post by leniII on 2010-02-03
I have received some aerial photograph-files in .ecw format and don't know how to deal with them. I installed grass gis because I hoped to be able to open these files with it. But for doing that the photographs need to be georeferenced and I just know the bottom right coordinates. How can I manage it to open these files without beeing georeferenced? Or otherwise is there any converter for changing .ecw to .jpg?

Thanks for any help!

---

### Post by hubie on 2010-02-03
[A quick check on Wikipedia]("http://en.wikipedia.org/wiki/ECW_(file_format)") shows compatible software.  Glancing at the list, it looks like one free option would be to use IrfanView on a Win machine to convert it to something you can use.

Actually, a better option I just stumbled on is described on [this page]("http://www.cartotalk.com/index.php?showtopic=2357") where they talk about installing [gdal]("http://www.gdal.org/"), which is in the repositories.  You can then convert the file to some other format using the gdal_translate command.

---

### Post by asbesto on 2010-08-01
And, is there a tool just to open and show them on screen, maybe for printing some parts? I can't find one! :(

---

### Post by LTVCA on 2010-08-05
You could also try Quantum GIS.  However, you still need to have GDAL and ecw support installed to deal with the .ecw files.

---

### Post by asbesto on 2010-08-06
I found a solution and wrote a little HOWTO here in the forum:


[http://http://ubuntuforums.org/showthread.php?t=1543485]("http://http://ubuntuforums.org/showthread.php?t=1543485")

;)

---

