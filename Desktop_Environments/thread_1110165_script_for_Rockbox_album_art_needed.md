---
title: "script for Rockbox album art needed"
date: 2009-03-29
forum: Desktop Environments
---

### Post by nlz on 2009-03-29
Rockbox can show albumart when playing songs, but there are some things that have to be done:

1. All the images should be in *.bmp (whereas most album art is in *.jpg)

2. The file name should be    
   1.  ./filename.bmp
   2. ./albumtitle.bmp
   3. ./cover.bmp
   4. /.rockbox/albumart/artist-albumtitle.bmp
   5. ../albumtitle.bmp
   6. ../cover.bmp

So it would be great i there was a script (hint hint) which would make a jpg > bmp conversion and subsequently rename the title of the image into albumtitle.bmp, if there is already a imagefile in this directory, it can leave the imagename as it was.

I would be great if someone could write such a script. Thanks in advance.

---

### Post by nlz on 2009-03-29
> #!/bin/sh
# Scriptino di Federico Sette (C) 2004
for i in $(seq 1 9); do
convert 00$i.bmp 00$i.jpg
done
for j in $(seq 10 99); do
convert 0$j.bmp 0$j.jpg
done

Save the file as "convert.sh" and, from shell, do:
#chmod +x convert.sh

this from [here]("http://ubuntuforums.org/showthread.php?t=54261") should help, although the script should go recursively into the directories...

---

### Post by nlz on 2009-03-29
```
#!/bin/sh
find -iname "*.jpg" -o -iname "*.gif" -o -iname "*.png" | while read file
    do convert "$file" -thumbnail 130x130 "${file%.*}".bmp
done
```

almost there....

---

### Post by nlz on 2009-03-29
[http://vcardenasblog.blogspot.com/2008/09/album-art-extracter-for-rockbox.html](http://vcardenasblog.blogspot.com/2008/09/album-art-extracter-for-rockbox.html)

[http://www.box.net/shared/puulfdoaex](http://www.box.net/shared/puulfdoaex)

uchum.. here it is...

---

### Post by nlz on 2009-03-29
Cannot get the program to work, but the script works fine! It leaves the original jpg files in the directory, so one can correct stuff that goes wrong..

---

