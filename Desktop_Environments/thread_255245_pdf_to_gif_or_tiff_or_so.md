---
title: "pdf to gif or tiff or so"
date: 2006-09-11
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-11
Hey, I've got a pdf file created from gifs. After throwing away the gifs, I noticed the pdf file is 22MB. Far too much.

Now I'm looking for a way to reduce the size. I can think of two ways:

1) find a program that's got a pdf-shrink option (like gimp for images)
2) save the pdf as gifs of tiffs or so, re-size them, and then pdf them again.

Who knows how to do one of them or has a better idea?

Gabriel

---

### Post by ajgreeny on 2006-09-11
Imagemagick will do what you want, I think.  If I remember right, it is installed as part of the default in ubuntu (maybe only in kubuntu, which I use) but it will convert most image formats to another very easily and quickly, using the command line.  Don't be scared; when you have tried it a couple of times you will see how great the terminal/command line can be.

---

### Post by anthro398 on 2006-09-11
Yes, the specific command in Imagemagick is convert. You can change the density of the pdf using convert.  You'll have to 'man convert' as I don't recall the syntax.

---

### Post by GabrielWolff on 2006-09-11
Can't make it work.
It looks like this:
```
gabriel@gabriel:~/Noten/Piazzolla$ convert "Piazzolla - Chin Chin [pno, vln, guit, bndn, cb].pdf" "Piazzolla - Chin Chin [pno, vln, guit, bndn, cb].gif"
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
gabriel@gabriel:~/Noten/Piazzolla$
```

It's a multiple pages pdf document. Maybe that's why it doesn't work? There must be way around it, though...

G

---

### Post by ajgreeny on 2006-09-11
Have a look here:-
[http://www-128.ibm.com/developerworks/library/l-graf2/?ca=dgr-lnxw15GraphicsLine](http://www-128.ibm.com/developerworks/library/l-graf2/?ca=dgr-lnxw15GraphicsLine)
I think it may help you to do exactly what you want if you scroll down to the "PDF Handling" section.

---

### Post by GabrielWolff on 2006-09-11
***Naaaaaaaaa!!!***
```
gabriel@gabriel:~/Noten/Piazzolla$ convert "Piazzolla - Chin Chin [pno, vln, guit, bndn, cb].pdf" pages-%03d.pn
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
   **** ERROR: Unable to process JPXDecode data. Page will be missing data.
convert: unable to open module file `/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/pn.la': No such file or directory.
gabriel@gabriel:~/Noten/Piazzolla$
```

Think the problem is it ain't able to read the pdf or so...? I donno, but it doesn't work...

Huh??

Gabriel

---

